---
title: "Temel doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dd6f85dc7961a7c3fd51e67b9fd6e16de9faa41d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="basic-validation"></a>Temel doğrulama
Bu örnek bir etkinliğin oluşur `CreateProduct`, hangi doğrular, kendi `Cost` bağımsız değişkeni ' den küçük veya eşit kendi `Price` bağımsız değişkeni.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Doğrulama, (doğrulama mantığını etkinliği oluşturur) etkinlik yazar ve belirli bir iş akışında doğrulama hizmetlerini çağıran iş akışı yazarı kullanan iki yazarlar vardır. Bu senaryoda, etkinlik Yazar kendi etkinliği her örneği fiyat daha küçük veya buna eşit maliyet olmalıdır yaptırmak istiyor.  
  
 Etkinlik yazarın (iç etkinliği) gerekir:  
  
-   Kısıtlama oluşturma (`PriceGreaterThanCost`). Tüm doğrulama mantığını bulunduğu budur.  
  
-   Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama eklemek (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.  
  
 İş akışı yazarı (ana programı) gerekir:  
  
-   Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).  
  
-   Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.ValidationError>.  
  
-   (İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  BasicValidation.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`