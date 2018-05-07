---
title: Kısıtlama türleri
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 53e5975017c3a27ede8ad07cd93f78f71df2d3e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="constraint-types"></a>Kısıtlama türleri
Bu örnek bir iş akışına kısıtlamaları uygulamak için iki farklı yollar gösterir, bir gelen (yapı) etkinliği içinde ve bir gelen dışında (ilke) olur. Bu senaryoda, iki bağımsız değişkenler arasındaki ilişkiyi doğrulamak bir etkinlik yazar (3rth taraf yazılım şirketten) ister. Bu durumda, maliyet fiyatına eşit veya daha küçük olmalıdır. Genel doğrulama yapı kısıtlaması budur.  
  
 Ardından bir alışveriş sahibi bazı doğrulama Bu genel etkinlik eklemek istiyor. Bu durumda, çoğu $9.99 olmasını ürünlerinde veya daha az istediği. Bu nedenle, kendisinin üstünde olan bir ilke kısıtlaması kullanan `CreateProduct` etkinlik.  
  
 Örnek:  
  
 Etkinlik yazar (yapı) gerekir:  
  
-   Kısıtlama oluşturma (`PriceGreaterThanCost`). Tüm doğrulama mantığını bulunduğu budur.  
  
-   Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama eklemek (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.  
  
 İş akışı yazarı (ilke) gerekir:  
  
-   Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).  
  
-   Kısıtlama oluşturma (`MaxPrice`).  
  
-   Oluşturma bir <xref:System.Activities.Validation.ValidationSettings> örneği (`validationSettings`) ve kısıtlama eklemek (`MaxPrice`) koleksiyonuna `AdditionalConstraints`. Burada iş akışı yazarı ilke kısıtlamaları dizisi veya paralel gibi herhangi bir etkinlik ekleyebilirsiniz.  
  
-   Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.ValidationError> nesneleri.  
  
-   (İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  ConstraintTypes.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`