---
title: Hizmet Çerçevesi Meta Verileri
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f3e73df54b3389b2c9f27001953be147b27eb6f8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991211"
---
# <a name="service-framework-metadata"></a>Hizmet Çerçevesi Meta Verileri
Bu konu, Service Framework meta verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Asyncendcaltadonyanlışlıkla Gchannel|Yanlış kanalda zaman uyumsuz bir uç çağrıldı.|  
|Asyncendcalledwithanıasyncresult|Farklı bir Begin yönteminden IAsyncResult ile zaman uyumsuz bir End çağrıldı.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Belirtilen için anlaşma türü alınmaya çalışıldı. Tür ServiceContract değil ve ServiceContract almıyor.|  
|CannotHaveTwoOperationsWithTheSameName3|Aynı sözleşmede aynı ada sahip iki işlem olamaz. Belirtilen türdeki belirtilen metotlar bu kuralı ihlal ediyor. Yöntem adını değiştirerek veya OperationContractAttribute 'un Name özelliğini kullanarak işlemlerden birinin adını değiştirin.|  
|CannotInheritTwoOperationsWithTheSameName3|Aynı ada sahip iki farklı işlem devralınabilir. Belirtilen sözleşmelerdeki belirtilen işlem bu kuralı ihlal ediyor. Yöntem adını değiştirerek veya OperationContractAttribute 'un Name özelliğini kullanarak işlemlerden birinin adını değiştirin.|  
|CantCreateChannelWithManualAddressing|İstek/yanıt gerektiren bir anlaşma ve el ile adresleme gerektiren bir bağlama için yalnızca çift yönlü iletişimi destekleyen bir kanal oluşturulamaz.|  
|DuplicateBehavior1|Değer koleksiyona eklenemiyor. Koleksiyonda aynı belirtilen türde bir öğe zaten var. Bu koleksiyon, her türün yalnızca bir örneğini destekler.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Belirtilen temel hizmet sözleşmesinin belirtilen bir geri çağırma anlaşması olduğundan, belirtilen türetilmiş hizmet sözleşmesinin belirtilen tür ya da geri arama sözleşmesi olarak türetilmiş bir tür belirtmesi gerekir.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Belirtilen ServiceContract türünde belirtilen yöntem için geçersiz zaman uyumsuz Begin yöntemi imzası. Begin yönteminiz, son iki bağımsız değişken olarak bir AsyncCallback ve bir nesne almalıdır ve bir IAsyncResult döndürmelidir.|  
|InvalidAsyncEndMethodSignatureForMethod2|Belirtilen ServiceContract türünde belirtilen yöntem için geçersiz zaman uyumsuz bitiş yöntemi imzası. Bitiş yönteminiz, son bağımsız değişken olarak bir IAsyncResult almalıdır.|  
|MessagePropertiesArraySize0|Geçirilen dizide, bu koleksiyonun içerdiği tüm özellikleri tutmak için yeterli alan yok.|  
|OneWayAndFaultsIncompatible2|Belirtilen türdeki belirtilen yöntem IsOneWay = true olarak işaretlendi ve bir veya daha fazla FaultContractAttributes bildiriyor. Tek yönlü yöntemler FaultContractAttributes bildiremez. IsOneWay 'ı false olarak değiştirin veya FaultContractAttributes 'yi kaldırın.|  
|UnsupportedWSDLOnlyOneMessage|Desteklenmeyen Web Hizmetleri Açıklama Dili. Hata iletileri için yalnızca bir ileti bölümü desteklenir. Bu hata iletisi, birden fazla ileti bölümüne başvurur. Web Hizmetleri Açıklama Dili dosyasına düzenleme erişiminiz varsa, hata iletisi yalnızca bir bölüme başvurduğu için ek ileti parçalarını kaldırarak sorunu çözebilirsiniz.|  
|UnsupportedWSDLTheFault|Desteklenmeyen Web Hizmetleri Açıklama Dili. Hata iletisi bölümü bir öğeye başvurmalıdır. Bu hata iletisi bir öğeye başvurmuyor. Web Hizmetleri tanım dili belgesine yönelik düzenleme erişiminiz varsa, ' element ' özniteliğini kullanarak bir şema öğesine başvurarak sorunu çözebilirsiniz.|  
|Wsdlımporterrordependencydetail|Belirtilen diğer değerin bağımlı olduğu belirtilen içeri aktarılırken bir hata oluştu. XPath de belirtilir.|  
|XsdMissingRequiredAttribute1|Belirtilen gerekli öznitelik eksik.|
