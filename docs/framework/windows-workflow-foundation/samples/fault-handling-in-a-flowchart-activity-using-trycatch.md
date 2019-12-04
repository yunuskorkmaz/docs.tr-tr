---
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710830"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme

Bu örnek, <xref:System.Activities.Statements.TryCatch> etkinliğinin karmaşık bir denetim akışı etkinliği içinde nasıl kullanılabileceğini gösterir.

Bu örnekte, bir promosyon kodu ve alt öğe sayısı, promosyon koduna karşılık gelen formüle göre bir iskontoyu hesaplayan <xref:System.Activities.Statements.Flowchart> etkinliğe değişken olarak geçirilir. Örnek, örneğin, örnek kod ve iş akışı Tasarımcısı sürümlerini içerir.

Aşağıdaki tabloda `CreateFlowchartWithFaults` etkinliğinin değişkenleri ayrıntılı olarak verilmiştir.

|Parametreler|Açıklama|
|----------------|-----------------|
|promoCode|Promosyon kodu. Tür: dize<br /><br /> Parantez içinde Açıklama içeren olası değerler:<br /><br /> -Tek (tek)<br />-MNK (çocuk olmadan evli.)<br />-MWK (çocuklarla evli)|
|numKids|Alt öğe sayısı. Tür: int|

`CreateFlowchartWithFaults` etkinliği, `promoCode` bağımsız değişkenine geçiş yapan ve aşağıdaki formülü kullanarak indirimi hesaplayan <xref:System.Activities.Statements.FlowSwitch%601> etkinliğini kullanır.

|`promoCode` değeri|İndirim (%)|
|--------------------------|--------------------|
|Tek|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Note:** olası, bu hesaplama <xref:System.DivideByZeroException>oluşturabilir. Bu nedenle, indirim hesaplaması, <xref:System.DivideByZeroException> özel durumunu yakalayan ve iskontoyu sıfıra ayarlayan bir <xref:System.Activities.Statements.TryCatch> etkinliğine sarmalanır.|

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak FlowchartWithFaultHandling. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi İş Akışları](../flowchart-workflows.md)
- [Özel Durumlar](../exceptions.md)
