---
description: 'Daha fazla bilgi edinin: ServiceBehaviorAttribute'
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 57ffa9103523618db752b3be6d43bb16603d1728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715580"
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute

ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Syntax  
  
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

 ServiceBehaviorAttribute sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="automaticsessionshutdown"></a>Automaticsessionkapanıyor  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bir istemci bir çıkış oturumunu kapattığında, oturumun otomatik olarak kapatılıp kapatılmayacağını gösterir.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  

 Veri türü: dize  
Erişim türü: salt okunurdur  
  
 Bir hizmetin bir iş parçacığını, birden çok iş parçacığını veya yer aldığı çağrıları destekleyip desteklemediğini gösterir.  
  
### <a name="configurationname"></a>ConfigurationName  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmet yapılandırmasının adı.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bilinmeyen serileştirme verilerinin hatta gönderileceğini belirtir.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Yönetilen özel durum bilgilerinin, istemcilere hata ayıklama amacıyla döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirtir.  
  
### <a name="instancecontextmode"></a>InstanceContextMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Yeni bir hizmet nesnesinin ne zaman oluşturulacağını belirtir.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Seri hale getirilen bir nesnede izin verilen en fazla öğe sayısı.  
  
### <a name="name"></a>Name  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 WSDL içindeki hizmetin Name özniteliği.  
  
### <a name="namespace"></a>Ad Alanı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 WSDL 'de hizmetin hedef ad alanı.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Geçerli işlem tamamlandığında hizmet nesnesinin geri dönüştürülüp dönüştürülmeyeceğini belirtir.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Geçerli oturum kapandığında bekleyen işlemlerin tamamlanıp tamamlanmadığını belirtir.  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlem yalıtım düzeyini belirtir.  
  
### <a name="transactiontimeout"></a>Işlem zaman aşımı  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bir işlemin tamamlaması gereken dönem.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 İş parçacığı yürütmeyi seçmek için geçerli eşitleme kapsamının kullanılıp kullanılmayacağını belirtir.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Sistemin ya da uygulamanın SOAP MustUnderstand üst bilgi işlemeyi zorunlu yapıp uygulamamadığını belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
