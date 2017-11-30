---
title: "RangeEnumeration etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35bff923b0e8d6fe7c01cb7970c7b6ee46488a43
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="rangeenumeration-activity"></a>RangeEnumeration etkinliği
Bu örnek nasıl sayıların bir koleksiyon yineleme özel bir aktivite oluşturulacağını gösterir. Aşağıdaki tabloda örnek bulunan ana dosyalar ayrıntılarını verir.  
  
|Dosya adı|Açıklama|  
|---------------|-----------------|  
|RangeEnumeration.cs|Adlı özel bir aktivite tanımlar `RangeEnumeration` , geçersiz kılmalar <xref:System.Activities.NativeActivity> sınıfı ve bir dizi numarası aracılığıyla döngüleri.|  
|RangeEnumerationSample.cs|Kullanan bir istemci uygulaması `RangeEnumeration` sayıların koleksiyon üzerinde yinelenecek etkinlik.|  
  
 Aşağıdaki tabloda özelliklerini ayrıntıları `RangeEnumeration` etkinlik.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|Başlat|Döngüden başlatmak için tam sayı.|  
|Durdur|Döngü sırasında durdurmak için bir tamsayı.|  
|Adım|Her zaman yinelemek için ne kadar belirtir.|  
|Gövde|Her yineleme sırasında yürütülecek kod belirtir.|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RangeEnumeration.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`