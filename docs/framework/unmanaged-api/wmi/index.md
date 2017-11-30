---
title: "WMI ve performans sayaçları (yönetilmeyen API Başvurusu)"
description: ".NET Framework özetler yönetilmeyen API için WMI ve performans sayacı bilgileri."
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.date: 11/06/2017
ms.topic: article-type-from-white-list
ms.prod: .net-framework
ms.devlang: cpp
ms.openlocfilehash: 461d90aaf5beca1c0f1d1965ce0ea07411e56e79
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2017
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Yönetim Araçları (WMI) ve performans sayaçları (yönetilmeyen API Başvurusu)

.NET Framework WMI ve performans sayaçları yönetilmeyen API çağrıları sarmalamak işlevler kümesi oluşur [yerel Windows Yönetim Araçları'nı API](https://msdn.microsoft.com/library/aa389276(v=vs.85).aspx). Araçlar ve yönetmek ve uzak bilgisayar sistemleri izlemek kitaplıklar geliştirme sağlar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
API aşağıdaki işlevleri içerir:

| İşlev | Açıklama |
|---------|---------|
| [BeginEnumeration işlevi](beginenumeration.md) | Numaralayıcı WMI nesne özellikleri bir numaralandırmanın başlangıç durumuna sıfırlar. |
| [BeginMethodEnumeration işlevi](beginmethodenumeration.md) |  Bir nesne için kullanılabilen yöntemler numaralandırması başlar. |
| [BlessIWbemServices işlevi](blessiwbemservices.md) | Kullanıcı kimlik bilgilerini belirli bir IWbemServices sınıf erişime olup olmadığını gösterir. |
| [BlessIWbemServicesObject işlevi](blessiwbemservicesobject.md) | Kullanıcı kimlik bilgilerinin belirtilen IWbem servis nesnesi erişime olup olmadığını gösterir. |
| [Kopya işlevi](clone.md) | Geçerli nesnenin tam bir kopyası olan yeni bir nesne döndürür. |
| [CloneEnumWbemClassObject işlevi](cloneenumwbemclassobject.md) | Numaralandırma içindeki geçerli konumunu koruyarak bir numaralandırıcı mantıksal bir kopyasını oluşturur. |
| [CompareTo işlevi](compareto.md) | Nesneyi başka bir Windows Yönetim nesnesi için karşılaştırır. |
| [ConnectServerWmi işlevi](connectserverwmi.md) | Belirtilen bir bilgisayardaki bir WMI ad alanı için DCOM aracılığıyla yapılan bağlantı oluşturur. |
| [CreateClassEnumWmi işlevi](createclassenumwmi.md) | Belirtilen seçim ölçütü karşılayan tüm sınıflar için bir numaralandırıcı döndürür. |
| [CreateInstanceEnumWmi işlevi](createinstanceenumwmi.md) | Belirtilen bir sınıfın belirtilen seçim ölçütlerine intances döndüren bir numaralandırıcı döndürür. |
| [İşlev Sil](delete.md) | Belirtilen bir özelliği bir sınıf tanımı ve tüm alt niteleyicileri siler. |
| [DeleteMethod işlevi](deletemethod.md) | Belirtilen yöntem bir CIM sınıfı tanımından siler. |
| [Örneğin işlevi](endenumeration.md) | Bir numaralandırma sırasını sonlandırır. | 
| [EndMethodEnumeration işlevi](endmethodenumeration.md) | Çağrılarak başlatılan bir numaralandırma sırasını sonlandırır [BeginMethodEnumeration işlevi](beginmethodenumeration.md). |
| [ExecNotificationQueryWmi işlevi](execnotificationquerywmi.md) | Olaylarını almak için bir sorgu yürütür. |
| [ExecQueryWmi işlevi](execquerywmi.md) | Nesneleri almak için bir sorgu yürütür. |
| [FormatFromRawValue işlevi](formatfromrawvalue.md) | Biçim dönüştürmeyi zamana dayalı ise belirtilen biçime bir ham performans veri değeri veya iki ham performans veri değerleri dönüştürür. | 
| [Get işlevi](get.md) | Varsa belirtilen özellik değerini alır. |
| [GetCurrentApartmentType işlevi](getcurrentapartmenttype.md) | Arayan yürütülmekte olduğu Grup türünü alır. |
| [GetDemultiplexedStub işlevi](getdemultiplexedstub.md) | Windows Yönetimi'nden zaman uyumsuz çağrılar alırken bir istemci yardımcı olması için bir nesne iletici havuz oluşturur. |
| [Geterrorınfo işlevi](geterrorinfo.md) | Önceki işlev çağrısında hata bilgilerini alır. | 
| [GetMethod işlevi](getmethod.md) | Belirtilen yöntem bilgilerini alır. | 
| [GetMethodOrigin işlevi](getmethodorigin.md) | Bir yöntem olarak bildirilen sınıfı belirler. |
| [GetMethodQualifierSet işlevi](getmethodqualifierset.md) | Belirli bir yöntem için ayarlanmış niteleyicisi alır. |
| [GetNames işlevi](getnames.md) | Bir alt veya tümünü bir nesnenin özellik adlarını alır. |
| [GetObjectText işlevi](getobjecttext.md) | Bir nesnenin bir metinsel oluşturma MOF sözdiziminde döndürür. | 
| [GetPropertyHandle işlevi](getpropertyhandle.md) | Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür. |
| [GetPropertyOrigin işlevi](getpropertyorigin.md) | Bir özellik bildirilmedi sınıfı belirler. |
| [GetPropertyQualifierSet işlevi](getpropertyqualifierset.md) | Belirli bir özelliği için belirlenen niteleyicisi alır.  |
| [GetQualifierSet işlevi](getqualifierset.md) | Sınıf örneği veya bir sınıf tanımı için ayarlamak niteleyicisi alır. |
| [InheritsFrom işlevi](inheritsfrom.md) | Geçerli sınıf veya örnek belirtilen üst sınıftan türetilen olup olmadığını belirler. |
| [Initialize işlevi](initialize.md) | WMI başlatma gerçekleştirir. |
| [Next işlevi](next.md) | Bir listedeki sonraki özelliği alır. | 
| [NextMethod işlevi](nextmethod.md) | Numaralandırma sonraki yöntem alır. |
| [PUT işlevi](put.md) | Adlandırılmış bir özelliği için yeni bir değer ayarlar. |
| [PutClassWmi işlevi](putclasswmi.md) | Yeni bir sınıf oluşturur veya mevcut bir güncelleştirir. |
| [PutInstanceWmi işlevi](putinstancewmi.md) | Oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir. Örnek için WMI deposunun yazılır. |
| [PutMethod işlevi](putmethod.md) | Bir yöntem oluşturur. |
| [QualifierSet_BeginEnumeration işlevi](qualifierset-beginenumeration.md) | Bir nesnenin niteleyicileri numaralandırması sabit başlangıç durumuna sıfırlar. |
| [QualifierSet_Delete işlevi](qualifierset-delete.md) | Belirtilen bir niteleyici adıyla siler.  |
| [QualifierSet_EndEnumeration işlevi](qualifierset-endenumeration.md) | Çağrısıyla başlamış numaralandırması sonlandırır `QualifierSet_BeginEnumeration` işlevi. |
| [QualifierSet_Get işlevi](qualifierset-get.md) | Belirtilen adlandırılmış niteleyici alır.  |
| [QualifierSet_GetNames işlevi](qualifierset-getnames.md) | Tüm niteleyicileri veya geçerli nesne ya da özellik kullanılabilir belirtilen niteleyicileri adlarını alır. |
| [QualifierSet_Next işlevi](qualifierset-next.md) | Sonraki çağrı kullanmaya bir numaralandırma niteleyicisinde alır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi. |
| [QualifierSet_Put işlevi](qualifierset-put.md) | Değeri ve adlandırılmış niteleyicisi yazar. |
| [ResetSecurity işlevi](resetsecurity.md) | Sağlanan kimliğe bürünme belirteci geçerli iş parçacığına atar. |
| [SetSecurity işlevi](setsecurity.md) | Geçerli iş parçacığı ile ilişkili kimliğe bürünme belirtecini alır. |
| [SpawnDerivedClass işlevi](spawnderivedclass.md) | Belirtilen bir nesneden bir yeni türetilmiş bir sınıf oluşturur. | 
| [SpawnInstance işlevi](spawninstance.md) | Bir sınıfın yeni bir örneğini oluşturur. |   
| [VerifyClient işlevi](verifyclientkey.md) | İstemci anahtar doğru güvenlik sahip olmasını sağlar. |
| [WritePropertyValue işlevi](writepropertyvalue.md) | Bir özellik tanımlayıcısı tarafından tanımlanan bir özellik için belirtilen sayıda baytı yazar. |

 ## <a name="see-also"></a>Ayrıca bkz.
[Yönetilmeyen API Başvurusu](../index.md) 