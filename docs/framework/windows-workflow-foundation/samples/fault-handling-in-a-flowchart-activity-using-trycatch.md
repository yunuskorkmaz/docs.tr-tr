---
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 81bfeb911658a6f363a9f0f95ecc7db68a02dbe2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331266"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
Bu örnek, gösterir nasıl <xref:System.Activities.Statements.TryCatch> etkinliği bir karmaşık denetim akışı etkinliği içinde kullanılabilir.

 Bu örnekte, bir promosyon kodu ve alt öğe sayısı için değişkenleri olarak geçirilen bir <xref:System.Activities.Statements.Flowchart> promosyon kodunu için karşılık gelen formüllerini temel bir hesaplar etkinlik. Örnek, kesinlik temelli kod ve iş akışı Tasarımcısı sürümleri örneği içerir.

 Aşağıdaki tabloda değişkenleri ayrıntıları `CreateFlowchartWithFaults` etkinlik.

|Parametreler|Açıklama|
|----------------|-----------------|
|promoCode|Promosyon kodu. Tür: Dize<br /><br /> Parantez içindeki açıklama ile olası değerler:<br /><br /> -Tek (tek)<br />-MNK (Evli ile Çocuğunuz yok.)<br />-MWK (çocuk ile Evli.)|
|numKids|Alt öğelerin sayısı. Tür: int|

 `CreateFlowchartWithFaults` Etkinliği kullanan bir <xref:System.Activities.Statements.FlowSwitch%601> anahtarlarını etkinlik `promoCode` bağımsız değişken ve şu formülü kullanarak hesaplar.

|Değeri `promoCode`|İndirim (%)|
|--------------------------|--------------------|
|Tek|10|
|MNK|15|
|MWK|15 + (1-1 /`numberOfKids`)\*10 **Not:**  Bu hesaplama büyük olasılıkla oluşturabilecek bir <xref:System.DivideByZeroException>. Bu nedenle, indirim hesaplama içinde sarmalanmış bir <xref:System.Activities.Statements.TryCatch> yakalayan etkinlik <xref:System.DivideByZeroException> özel durum ve indirim sıfır olarak ayarlıyor.|

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak FlowchartWithFaultHandling.sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi İş Akışları](../flowchart-workflows.md)
- [Özel Durumlar](../exceptions.md)
