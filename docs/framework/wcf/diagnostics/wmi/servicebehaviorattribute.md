---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 420686ebda7f23a5d883deece251b034147fafa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654587"
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceBehaviorAttribute sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Otomatik olarak bir istemci bir çıkış oturumu kapattığı zaman oturumu kapatmak görüntülenip görüntülenmeyeceğini gösterir.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Veri türü: dize  
Erişim türü: salt okunur  
  
 Bir hizmet tek bir iş parçacığı, birden çok iş parçacığı veya yeniden girilen çağrıları destekleyip desteklemediğini belirtir.  
  
### <a name="configurationname"></a>ConfigurationName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hizmet yapılandırmasının adı.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bilinmeyen serileştirme verilerinin gönderilip gönderilmeyeceğini belirtir.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hata ayıklama amacıyla, istemcilere dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirtir.  
  
### <a name="instancecontextmode"></a>InstanceContextMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Yeni bir hizmet nesnesi oluşturulduğunda belirtir.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Serileştirilmiş nesne içinde izin verilen öğe sayısı.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmetinde öğesinin ad özniteliği.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmetinde hedef ad alanı.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Geçerli işlem tamamlandıktan sonra hizmet nesnesi geri olup olmadığını belirtir.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Geçerli oturumu kapattığında bekleyen işlem tamamlanıp tamamlanmadığını belirtir.  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İşlem yalıtım düzeyi belirtir.  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 İçinde bir işlemin tamamlanması gereken süre.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Geçerli eşitleme kapsamının iş parçacığı yürütmeyi seçmek için kullanılıp kullanılmayacağını belirtir.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Sistem veya uygulama SOAP MustUnderstand üst bilgi işleme uygulayıp uygulamayacağını belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
