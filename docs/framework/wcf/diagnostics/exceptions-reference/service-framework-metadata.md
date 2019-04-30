---
title: Hizmet Çerçevesi Meta Verileri
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f65f53ff99202275876fb6e3c431bc49ae2bd38b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780806"
---
# <a name="service-framework-metadata"></a>Hizmet Çerçevesi Meta Verileri
Bu konu hizmet çerçevesi meta verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Zaman uyumsuz bir End yanlış kanalda çağrıldı.|  
|AsyncEndCalledWithAnIAsyncResult|Zaman uyumsuz bir End IAsyncResult ile farklı bir Begin metodundan çağrıldı.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Belirtilen anlaşma türü alınmaya çalışıldı. Tür bir ServiceContract değil ve bir ServiceContract devralmıyor.|  
|CannotHaveTwoOperationsWithTheSameName3|İki işlem aynı adla aynı anlaşmaya sahip olamaz. Belirtilen türü belirtilen yöntem, bu kuralı ihlal ediyor. Metot adını değiştirerek veya OperationContractAttribute Name özelliğini kullanarak işlemlerden adını değiştirin.|  
|CannotInheritTwoOperationsWithTheSameName3|Aynı ada sahip iki farklı işlem devralınamaz. Belirtilen sözleşme belirtilen işlemi bu kuralı ihlal ediyor. Metot adını değiştirerek veya OperationContractAttribute Name özelliğini kullanarak işlemlerden adını değiştirin.|  
|CantCreateChannelWithManualAddressing|İstek/yanıt ve el ile adresleme gerektiren, ancak yalnızca çift yönlü iletişimi destekleyen bir bağlama gerektiren bir sözleşme için bir kanal oluşturulamıyor.|  
|DuplicateBehavior1|Değer koleksiyona eklenemiyor. Koleksiyon zaten aynı belirtilen türden bir öğe içeriyor. Bu koleksiyon, yalnızca her türün bir örneğini destekler.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Belirtilen temel hizmet sözleşmesi belirtilen geri çağırma anlaşması olduğundan, belirtilen türetilmiş hizmet sözleşmesi de, geri çağırma anlaşması belirtilen tür veya türetilmiş bir tür belirtmelisiniz.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Geçersiz zaman uyumsuz Begin metodu imzası için belirtilen ServiceContract türündeki belirtilen yöntem. Başlayan yöntemi en son iki bağımsız değişken olarak bir AsyncCallback ve bir nesne almak ve bir IAsyncResult döndürmelidir.|  
|InvalidAsyncEndMethodSignatureForMethod2|Geçersiz zaman uyumsuz End metodu imzası için belirtilen ServiceContract türündeki belirtilen yöntem. Son yönteminizi son bağımsız değişken olarak bir IAsyncResult almalıdır.|  
|MessagePropertiesArraySize0|Geçirilen dizi bu koleksiyonda bulunan özelliklerin tümünü tutacak yeterli yer yok.|  
|OneWayAndFaultsIncompatible2|Belirtilen yöntemde belirtilen tür IsOneWay işaretlenmiş = true ayarına ve bir ya da birkaç FaultContractAttributes bildiriyor. One-Way metotları, FaultContractAttributes bildiremez. IsOneWay değerini false olarak değiştirin ya da FaultContractAttributes öğesini kaldırın.|  
|UnsupportedWSDLOnlyOneMessage|Desteklenmeyen Web Hizmetleri Açıklama Dili. Hata iletileri için yalnızca bir ileti bölümü desteklenir. Bu hata iletisi, birden çok ileti bölümüne başvurur. Web Hizmetleri Açıklama Dili dosyasına düzenleme erişimi varsa, ileti başvuruları yalnızca bir bölüme ek ileti bölümlerini kaldırarak sorunu düzeltebilirsiniz.|  
|UnsupportedWSDLTheFault|Desteklenmeyen Web Hizmetleri Açıklama Dili. Hata iletisi bölümü bir öğeye başvuru gerekir. Bu hata iletisi bir öğeye başvurmuyor. Web Hizmetleri tanım dili belge düzenleme erişimi varsa 'element' özniteliğini kullanarak bir şema öğesine başvuru sorunu düzeltebilirsiniz.|  
|WsdlImportErrorDependencyDetail|Belirtilen içeri aktarılırken bir hata oluştu. belirtilen bir değere bağımlı olduğunu. Xpath da belirtilir.|  
|XsdMissingRequiredAttribute1|Gerekli öznitelik belirtilen eksik.|
