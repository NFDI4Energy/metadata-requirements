---
hide:
  - navigation
  - toc
---
# Requirement Table

<table id="requirements-table-id" class="mdl-data-table"></table>
<script src="https://cdn.datatables.net/v/dt/jq-3.7.0/jszip-3.10.1/dt-2.2.1/af-2.7.0/b-3.2.0/b-colvis-3.2.0/b-html5-3.2.0/b-print-3.2.0/cr-2.0.4/date-1.5.5/fc-5.0.4/fh-4.0.1/kt-2.12.1/r-3.0.3/rg-1.5.1/rr-1.5.0/sc-2.4.3/sb-1.8.1/sp-2.3.3/sl-3.0.0/sr-1.4.1/datatables.min.js"></script>

<script src="../../csv-parser.js"></script>
<script>
    window.fetch('../requirements.csv').then(response => response.text()).then(text => {
        let array = CSVToArray(text).filter(row => {
            const comparison = row.length != 1 || row[0] !== ''
            return comparison;
        });
        // the following code does produce a list of dicts as table data
        // const dictData = array.slice(1).map(row => {
        //     return array[0].reduce((acc, key, i) => {
        //         acc[key] = row[i];
        //         return acc;
        //     }, {});
        // });
        let data = {
            data: array.slice(1),
            columns: array[0].map(x => { return {title: x} }),
            // the following is an alternative when using dict based data
            // data: dictData,
            // columns: array[0].map(x => { return {data: x, title: x} }),
            layout: {
                top1Start: {
                    buttons: [
                        'copy', 'excel',
                        {
                            extend: 'searchPanes',
                            config: {
                                cascadePanes: true
                            }
                        },
                        'colvis'
                    ]
                }
            },
            // required to control which columns shall have a search Pane filter
            // sadly it does not work to disable all and just enable some
            columnDefs: [
                // {
                //     searchPanes: {
                //         show: false
                //     },
                //     targets: '_all'
                // },
                {
                    searchPanes: {
                        show: true
                    },
                    targets: [6,7,10,11]
                },
                {
                    searchPanes: {
                        show: false
                    },
                    targets: [0,1,2,3,4,5,8,9,12,13]
                }
            ],
            // allows to print groupings in the table
            //  but it only looks good if also a sorting is applied properly
            // rowGroup: {
            //     dataSrc: [1, 2]
            // },
            // autoFill: true,  // only relevant if editing
            // altnernative to responsive design:
            // fixedColumns: true,
            // scrollX: true,
            responsive: true,
            colReorder: true,
            rowReorder: true,
            fixedHeader: true,
            keys: true, // allows arrow key navigation and easy cell copy
            select: true  // required for searchPanes
        }
        let table = new DataTable('#requirements-table-id', data);
    });
    
</script>
