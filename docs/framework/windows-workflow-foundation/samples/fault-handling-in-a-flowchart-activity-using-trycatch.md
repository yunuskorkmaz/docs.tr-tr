---
description: 'Daha fazla bilgi edinin: bir akış çizelgesi etkinliğinde TryCatch kullanarak hata Işleme'
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 9ab323117e5b26696a07624117e8acc8c0beacff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755358"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme

Bu örnek, <xref:System.Activities.Statements.TryCatch> etkinliğin karmaşık bir denetim akışı etkinliği içinde nasıl kullanılabileceğini gösterir.

Bu örnekte, promosyon kodu ve alt öğe sayısı, <xref:System.Activities.Statements.Flowchart> promosyon koduna karşılık gelen formüle göre bir iskontoyu hesaplayan bir etkinliğe değişken olarak geçirilir. Örnek, örneğin, örnek kod ve iş akışı Tasarımcısı sürümlerini içerir.

Aşağıdaki tabloda etkinlik değişkenlerinin ayrıntıları verilmiştir `CreateFlowchartWithFaults` .

|Parametreler|Description|
|----------------|-----------------|
|promoCode|Promosyon kodu. Türü: Dize<br /><br /> Parantez içinde Açıklama içeren olası değerler:<br /><br /> -Tek (tek)<br />-MNK (çocuk olmadan evli.)<br />-MWK (çocuklarla evli)|
|numKids|Alt öğe sayısı. Tür: int|

`CreateFlowchartWithFaults`Etkinlik, <xref:System.Activities.Statements.FlowSwitch%601> `promoCode` bağımsız değişkene geçiş yapan ve aşağıdaki formülü kullanarak indirimi hesaplayan bir etkinlik kullanır.

|Değeri `promoCode`|İndirim (%)|
|--------------------------|--------------------|
|Tek|10|
|MNK|15|
|MWK|15 + (1 – 1/ `numberOfKids` ) \* 10 **Note:**  potansiyel olarak bu hesaplama bir oluşturabilir <xref:System.DivideByZeroException> . Bu nedenle, indirim hesaplaması <xref:System.Activities.Statements.TryCatch> özel durumu yakalayan bir etkinliğe sarmalanır <xref:System.DivideByZeroException> ve iskontoyu sıfıra ayarlar.|

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak FlowchartWithFaultHandling. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi İş Akışları](../flowchart-workflows.md)
- [Özel durumlar](../exceptions.md)
