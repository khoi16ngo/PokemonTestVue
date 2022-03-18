<template>
    <div>
        <!-- <div class>
            <img src="/src/assets/pokemon-logo.png" />
        </div> -->
        
        <div>
            <p>
                {{ diff.month }}:{{ diff.day }}:{{ diff.hour }}:{{ diff.minute }}:{{ diff.second }}
                until
                {{ formatDate(futureDate) }}
            </p>
        </div>

        <div>
            <p>
                JOIN THE HELLDOG FAMILY
            </p>
        </div>
    
    </div>
</template>

<script>
    const futureDate = new Date(2050, 0, 1);
    const getDateDiff = (date1, date2) => {
  const diff = new Date(date2.getTime() - date1.getTime());
  return {
    month: diff.getUTCMonth()*12,
    day: diff.getUTCDate() - 1,
    hour: diff.getUTCHours(),
    minute: diff.getUTCMinutes(),
    second: diff.getUTCSeconds(),
  };
};
export default {
    name: "Header",
    data() {
        return {
            futureDate,
            diff: {},
            timer: undefined,
        };
    },
    methods: {
        getDiff() {
            this.diff = getDateDiff(new Date(), futureDate);
        },
        formatDate(date) {
            let d = new Date(date), month = (d.getMonth() + 1).toString(), day = d.getDate().toString(), year = d.getFullYear().toString();
            if (month.length < 2)
                month = "0" + month;
            if (day.length < 2)
                day = "0" + day;
            return [year, month, day].join("-");
        },
    },
    beforeMount() {
        this.timer = setInterval(this.getDiff, 1000);
    },
    beforeUnmount() {
        clearInterval(this.timer);
    }
};
</script>