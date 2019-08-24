---
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016027"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme

Bu örnek, <xref:System.Activities.Statements.TryCatch> etkinliğin karmaşık bir denetim akışı etkinliği içinde nasıl kullanılabileceğini gösterir.

Bu örnekte, promosyon kodu ve alt öğe sayısı, promosyon koduna karşılık gelen formüle göre bir <xref:System.Activities.Statements.Flowchart> iskontoyu hesaplayan bir etkinliğe değişken olarak geçirilir. Örnek, örneğin, örnek kod ve iş akışı Tasarımcısı sürümlerini içerir.

Aşağıdaki tabloda `CreateFlowchartWithFaults` etkinlik değişkenlerinin ayrıntıları verilmiştir.

|Parametreler|Açıklama|
|----------------|-----------------|
|promoCode|Promosyon kodu. Tür: Dize<br /><br /> Parantez içinde Açıklama içeren olası değerler:<br /><br /> -Tek (tek)<br />-MNK (çocuk olmadan evli.)<br />-MWK (çocuklarla evli)|
|numKids|Alt öğe sayısı. Tür: int|

Etkinlik, `promoCode` bağımsız değişkene <xref:System.Activities.Statements.FlowSwitch%601> geçiş yapan ve aşağıdaki formülü kullanarak indirimi hesaplayan bir etkinlik kullanır. `CreateFlowchartWithFaults`

|Değeri`promoCode`|İndirim (%)|
|--------------------------|--------------------|
|Tek|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potansiyel olarak, bu hesaplama bir <xref:System.DivideByZeroException>oluşturabilir. Bu nedenle, indirim hesaplaması <xref:System.Activities.Statements.TryCatch> <xref:System.DivideByZeroException> özel durumu yakalayan bir etkinliğe sarmalanır ve iskontoyu sıfıra ayarlar.|

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak FlowchartWithFaultHandling. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi İş Akışları](../flowchart-workflows.md)
- [Özel Durumlar](../exceptions.md)
