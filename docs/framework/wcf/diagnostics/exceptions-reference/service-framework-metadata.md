---
title: "Hizmet Çerçevesi Meta Verileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3ab689a6a0d9bf91582ced3435439061c655d10e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="service-framework-metadata"></a>Hizmet Çerçevesi Meta Verileri
Bu konu hizmet çerçevesi meta verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Zaman uyumsuz bir son yanlış kanalda çağrıldı.|  
|AsyncEndCalledWithAnIAsyncResult|Zaman uyumsuz sonuç bir IAsyncResult ile farklı bir Begin yönteminden çağrıldı.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Sözleşme türü için belirtilen alınmaya çalışıldı. Tür bir ServiceContract değil ve bir ServiceContract devralmıyor.|  
|CannotHaveTwoOperationsWithTheSameName3|İki işlem, aynı sözleşme aynı ada sahip olamaz. Belirtilen tür belirtilen yöntemlere bu kural ihlal ediyor. Yöntem adını değiştirme veya OperationContractAttribute adını kullanarak işlemlerden biri adını değiştirin.|  
|CannotInheritTwoOperationsWithTheSameName3|Aynı ada sahip iki farklı işlemler devralır olamaz. Belirtilen sözleşmeleri belirtilen işlemi bu kuralı ihlal ediyor. Yöntem adını değiştirme veya OperationContractAttribute adını kullanarak işlemlerden biri adını değiştirin.|  
|CantCreateChannelWithManualAddressing|Bir istek/yanıt ve el ile adresleme gerektiriyor, ancak yalnızca çift yönlü iletişimi destekleyen bir bağlama gerektiren bir sözleşme için bir kanal oluşturulamıyor.|  
|DuplicateBehavior1|Değer koleksiyonuna eklenemez. Koleksiyon zaten aynı belirtilen türde bir öğe içeriyor. Bu koleksiyon yalnızca her türünün bir örneği destekler.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Belirtilen temel hizmet sözleşmesi belirtilen geri arama sözleşmesi olduğundan, belirtilen türetilen hizmet sözleşmesi ayrıca belirtilen türe veya türetilmiş bir tür geri çağırma sözleşmesi belirtmeniz gerekir.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Zaman uyumsuz başlangıç yöntemi için geçersiz imzası belirtilen belirtilen ServiceContract yazın. Başlamak yöntemi son iki bağımsız değişken olarak bir AsyncCallback ve bir nesne getirin ve bir IAsyncResult döndürmelidir.|  
|InvalidAsyncEndMethodSignatureForMethod2|Zaman uyumsuz son yöntemi için geçersiz imzası belirtilen belirtilen ServiceContract yazın. End yöntemi son bağımsız değişkeni olarak bir IAsyncResult almanız gerekir.|  
|MessagePropertiesArraySize0|Geçirilen dizi bu koleksiyonda bulunan tüm özellikleri tutmak için yeterli alan yok.|  
|OneWayAndFaultsIncompatible2|Belirtilen türdeki belirtilen yöntem IsOneWay işaretlenmiş = true ve bir veya daha fazla FaultContractAttributes bildiriyor. Tek yönlü yöntemleri FaultContractAttributes bildiremezsiniz. IsOneWay yanlış olarak değiştirin ya da FaultContractAttributes öğesini kaldırın.|  
|UnsupportedWSDLOnlyOneMessage|Desteklenmeyen Web Hizmetleri Açıklama Dili. Tek bir ileti bölümü hata iletileri için desteklenir. Bu hata iletisi için birden fazla ileti bölümü başvuruyor. Web Hizmetleri Açıklama Dili dosyasına düzenleme erişiminiz varsa, ileti başvuruları yalnızca bir bölümü arıza gibi ek ileti bölümlerini kaldırarak sorunu düzeltebilirsiniz.|  
|UnsupportedWSDLTheFault|Desteklenmeyen Web Hizmetleri Açıklama Dili. Hata iletisi bölümü bir öğeye başvuru gerekir. Bu hata iletisi, bir öğeye başvurmuyor. Web Hizmetleri tanımlama dili belge düzenleme erişiminiz varsa 'element' özniteliğini kullanarak şema öğesi başvurarak sorunu düzeltebilirsiniz.|  
|WsdlImportErrorDependencyDetail|Belirtilen alınırken bir hata oluştu diğer belirtilen değere bağlı olduğundan. Xpath da belirtilmiş.|  
|XsdMissingRequiredAttribute1|Belirtilen eksik özniteliği gerekli.|
