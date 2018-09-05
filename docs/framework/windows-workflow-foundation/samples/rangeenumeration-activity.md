---
title: RangeEnumeration etkinliği
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556298"
---
# <a name="rangeenumeration-activity"></a>RangeEnumeration etkinliği
Bu örnek, sayıdan oluşan bir koleksiyon yineleme özel bir etkinlik oluşturma işlemini gösterir. Aşağıdaki tabloda, örnekte bulunan ana dosyaları ayrıntıları.  
  
|Dosya adı|Açıklama|  
|---------------|-----------------|  
|RangeEnumeration.cs|Adlı özel bir etkinlik tanımlar `RangeEnumeration` , geçersiz kılmalar <xref:System.Activities.NativeActivity> sınıfı ve bir dizi numarası döner.|  
|RangeEnumerationSample.cs|Kullanan bir istemci uygulamanın `RangeEnumeration` sayıdan oluşan bir koleksiyon üzerinde yinelemek için etkinlik.|  
  
 Aşağıdaki tabloda özelliklerine ilişkin ayrıntılar `RangeEnumeration` etkinlik.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|Başlat|Döngüden başlatmak için bir tamsayı.|  
|Durdur|Döngü, durdurmak için bir tamsayı.|  
|Adım|Her yineleme yapmak için ne kadar belirtir.|  
|Gövde|Her yineleme sırasında yürütülecek kodu belirtir.|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RangeEnumeration.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`