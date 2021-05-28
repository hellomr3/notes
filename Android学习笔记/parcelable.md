plugins{
    id 'kotlin-parcelize'
}

## hint1
使用@Parcelize时不可空字段为空时会导致intent.getParcelableArrayListExtra报空指针异常