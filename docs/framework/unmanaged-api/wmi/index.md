---
title: WMI ve performans sayaçları (yönetilmeyen API Başvurusu)
description: .NET Framework özetler yönetilmeyen API için WMI ve performans sayacı bilgileri.
author: rpetrusha
ms.author: ronpet
ms.date: 11/06/2017
ms.openlocfilehash: bbf22496098f848cc7c55652198d792c6f631c15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049316"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Yönetim Araçları (WMI) ve performans sayaçları (yönetilmeyen API Başvurusu)

.NET Framework WMI ve performans sayaçları yönetilmeyen API çağrılar sarmalama işlevler kümesi oluşur [yerel Windows Yönetim Araçları'nı API](/windows/desktop/WmiSdk/com-api-for-wmi). Araçları ve kitaplıklarını yönetme ve izleme uzak bilgisayar sistemleri geliştirmenizi sağlar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

API aşağıdaki işlevleri içerir:

| İşlev | Açıklama |
|---------|---------|
| [BeginEnumeration işlevi](beginenumeration.md) | Numaralandırıcı nesne özellikleri WMI numaralandırması başlangıcına sıfırlar. |
| [BeginMethodEnumeration işlevi](beginmethodenumeration.md) |  Bir nesne için kullanılabilen yöntemler numaralandırması başlar. |
| [BlessIWbemServices işlevi](blessiwbemservices.md) | Kullanıcı kimlik bilgilerini belirtilen bir IWbemServices sınıfı erişime olup olmadığını gösterir. |
| [BlessIWbemServicesObject işlevi](blessiwbemservicesobject.md) | Kullanıcı kimlik bilgilerini belirtilen IWbem servis nesnesi erişime olup olmadığını gösterir. |
| [Clone işlevi](clone.md) | Geçerli nesnenin tam bir kopyası olan yeni bir nesne döndürür. |
| [CloneEnumWbemClassObject işlevi](cloneenumwbemclassobject.md) | Numaralandırma içindeki geçerli konumu koruma Numaralandırıcı mantıksal bir kopyasını oluşturur. |
| [CompareTo işlevi](compareto.md) | Başka bir Windows Yönetim nesnesi için bir nesne ile karşılaştırır. |
| [ConnectServerWmi işlevi](connectserverwmi.md) | Belirtilen bir bilgisayardaki bir WMI ad alanına DCOM aracılığıyla yapılan bağlantı oluşturur. |
| [CreateClassEnumWmi işlevi](createclassenumwmi.md) | Belirtilen seçim kriterleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür. |
| [CreateInstanceEnumWmi işlevi](createinstanceenumwmi.md) | Belirtilen seçim ölçütlerine belirli bir sınıf örneğini döndüren bir numaralandırıcı döndürür. |
| [Delete işlevi](delete.md) | Belirtilen özellik, bir sınıf tanımı ve tüm alt niteleyicileri siler. |
| [DeleteMethod işlevi](deletemethod.md) | Belirtilen bir yöntemdeki bir CIM sınıfı tanımını siler. |
| [EndEnumeration işlevi](endenumeration.md) | Bir numaralandırma sıralı sonlandırır. |
| [EndMethodEnumeration işlevi](endmethodenumeration.md) | Çağırarak başlatılan bir numaralandırma sırasını sonlandırıyor [BeginMethodEnumeration işlevi](beginmethodenumeration.md). |
| [ExecNotificationQueryWmi işlevi](execnotificationquerywmi.md) | Olayları almak için bir sorgu yürütür. |
| [ExecQueryWmi işlevi](execquerywmi.md) | Nesneleri almak için bir sorgu yürütür. |
| [FormatFromRawValue işlevi](formatfromrawvalue.md) | Biçim dönüştürme, zamana bağlı ise belirtilen biçimde bir ham performans veri değerine ya da iki ham performans veri değerleri dönüştürür. |
| [Get işlevi](get.md) | Varsa belirtilen özellik değerini alır. |
| [GetCurrentApartmentType işlevi](getcurrentapartmenttype.md) | Arayan içinde yürütüyor Grup türünü alır. |
| [GetDemultiplexedStub işlevi](getdemultiplexedstub.md) | Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için nesne ileticisi havuzu oluşturur. |
| [Geterrorınfo işlevi](geterrorinfo.md) | Önceki işlev çağrısında hata bilgilerini alır. |
| [GetMethod işlevi](getmethod.md) | Belirtilen yöntem hakkındaki bilgileri alır. |
| [GetMethodOrigin işlevi](getmethodorigin.md) | Bir yöntem içinde bildirildiği sınıf belirler. |
| [GetMethodQualifierSet işlevi](getmethodqualifierset.md) | Belirli bir yöntem için ayarlanmış niteleyicisi alır. |
| [GetNames işlevi](getnames.md) | Bir alt veya tümünü bir nesnenin özellik adlarını alır. |
| [GetObjectText işlevi](getobjecttext.md) | Bir nesnenin değerinin metinsel bir işleme MOF sözdiziminde döndürür. |
| [GetPropertyHandle işlevi](getpropertyhandle.md) | Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür. |
| [GetPropertyOrigin işlevi](getpropertyorigin.md) | Bir özellik içinde bildirildiği sınıf belirler. |
| [GetPropertyQualifierSet işlevi](getpropertyqualifierset.md) | Belirli bir özellik için ayarlanmış niteleyicisi alır.  |
| [GetQualifierSet function](getqualifierset.md) | Bir sınıf örneği veya bir sınıf tanımı için ayarlanmış niteleyicisi alır. |
| [InheritsFrom işlevi](inheritsfrom.md) | Geçerli sınıf veya örnek belirtilen üst sınıftan türetilen olup olmadığını belirler. |
| [Initialize işlevi](initialize.md) | WMI başlatma gerçekleştirir. |
| [Next işlevi](next.md) | Bir listedeki sonraki özelliği alır. |
| [NextMethod işlevi](nextmethod.md) | Sonraki yöntem bir sabit listesi alır. |
| [Put işlevi](put.md) | Adlandırılmış bir özelliği, yeni değere ayarlar. |
| [PutClassWmi işlevi](putclasswmi.md) | Yeni bir sınıf oluşturur veya mevcut olanı güncelleştirir. |
| [PutInstanceWmi işlevi](putinstancewmi.md) | Oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir. Örneği, WMI deposuna yazılır. |
| [PutMethod işlevi](putmethod.md) | Bir metot oluşturur. |
| [QualifierSet_BeginEnumeration işlevi](qualifierset-beginenumeration.md) | Bir nesnenin niteleyicileri numaralandırması sabit başlangıcına sıfırlar. |
| [QualifierSet_Delete işlevi](qualifierset-delete.md) | Belirtilen bir niteleyici adıyla siler.  |
| [QualifierSet_EndEnumeration işlevi](qualifierset-endenumeration.md) | Bir çağrı ile başlamış numaralandırma sonlandırır `QualifierSet_BeginEnumeration` işlevi. |
| [QualifierSet_Get işlevi](qualifierset-get.md) | Belirtilen adlandırılmış niteleyicisi alır.  |
| [QualifierSet_GetNames function](qualifierset-getnames.md) | Tüm niteleyicileri veya geçerli nesne ya da özellik kullanılabilir belirtilen niteleyicileri adlarını alır. |
| [QualifierSet_Next işlevi](qualifierset-next.md) | Bir çağrı ile başlatılan bir listedeki sonraki niteleyicisi alır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi. |
| [QualifierSet_Put işlevi](qualifierset-put.md) | Değer ve adlandırılmış niteleyicisi yazar. |
| [ResetSecurity işlevi](resetsecurity.md) | Sağlanan kimliğe bürünme belirteci için geçerli iş parçacığı atar. |
| [SetSecurity işlevi](setsecurity.md) | Geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini alır. |
| [SpawnDerivedClass işlevi](spawnderivedclass.md) | Belirtilen bir nesneden bir yeni türetilmiş bir sınıf oluşturur. |
| [SpawnInstance işlevi](spawninstance.md) | Bir sınıfın yeni bir örneğini oluşturur. |
| [VerifyClient işlevi](verifyclientkey.md) | İstemci anahtarı doğru güvenlik sahip olmasını sağlar. |
| [WritePropertyValue işlevi](writepropertyvalue.md) | Belirtilen sayıda baytı bir özellik tanımlayıcısı tarafından tanımlanan bir özellik yazar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen API Başvurusu](../index.md)
