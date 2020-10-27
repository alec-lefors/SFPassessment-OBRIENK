function doPaging(currentPageInput) {

    let currentPage = currentPageInput, // input
        range       = 5,  // amount of links displayed
        totalPages  = 20, // determined by amount of items, hardcoded for readability
        start       = 1;  // default

    let paging = [];      // output variable

    // Don't use negative values, force start at 1
    if (currentPage < (range / 2) + 1 ) {
        start = 1;

    // Don't go beyond the last page
    } else if (currentPage >= (totalPages - (range / 2) )) {
        start = Math.floor(totalPages - range + 1);

    } else {
        start = (currentPage - Math.floor(range / 2));
    }

    for (let i = start; i <= ((start + range) - 1); i++) {
        if (i === currentPage) {
            paging.push(`[${i}]`); // add brackets to indicate current page
        } else {
            paging.push(i.toString());
        }
    }
    return paging;
}
