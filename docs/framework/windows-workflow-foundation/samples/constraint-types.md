---
title: Kısıtlama türleri
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506618"
---
# <a name="constraint-types"></a>Kısıtlama türleri
Bu örnek, bir iş akışı kısıtlamaları uygulamak için iki farklı yol gösterir, bir etkinlik içinde (derleme) arasındadır ve bir gelen dışında (ilke) olur. Bu senaryoda, bir etkinlik yazar (şirketten 3rth taraf yazılım) iki bağımsız değişken arasındaki ilişkiyi doğrulamak istiyor. Bu durumda, maliyet fiyatına eşit veya değerinden küçük olmalıdır. Genel bir doğrulama yapı kısıtlaması budur.  
  
 Ardından bu genel etkinlik bazı doğrulama eklemek bir Atölye sahibi istiyor. Bu durumda, çoğu ürünlerinden $9.99 olması veya daha az istediği. Bu nedenle, üstünde olan bir ilke kısıtlaması kullandığı `CreateProduct` etkinlik.  
  
 Örnek:  
  
 Etkinlik yazar (derleme) gerekir:  
  
-   Kısıtlama oluşturma (`PriceGreaterThanCost`). Doğrulama mantığını bulunduğu budur.  
  
-   Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama ekleyin (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.  
  
 İş akışı yazar (ilke) gerekir:  
  
-   Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).  
  
-   Kısıtlama oluşturma (`MaxPrice`).  
  
-   Oluşturma bir <xref:System.Activities.Validation.ValidationSettings> örneği (`validationSettings`) ve kısıtlama ekleyin (`MaxPrice`) koleksiyonuna `AdditionalConstraints`. Burada iş akışı Yazar ilke kısıtlamaları sıralı veya paralel gibi herhangi bir etkinlik ekleyebilirsiniz.  
  
-   Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonunu <xref:System.Activities.Validation.ValidationError> nesneleri.  
  
-   (İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  ConstraintTypes.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`