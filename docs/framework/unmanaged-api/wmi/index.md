---
title: WMI ve performans sayaçları (yönetilmeyen API Başvurusu)
description: WMI ve performans sayacı bilgileri için .NET Framework yönetilmeyen API 'YI özetler.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127416"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Yönetim Araçları (WMI) ve performans sayaçları (yönetilmeyen API Başvurusu)

.NET Framework WMI ve performans sayaçları yönetilmeyen API, çağrıları [yerel WINDOWS YÖNETIM araçları API](/windows/desktop/WmiSdk/com-api-for-wmi)'sine kaydıramayan bir işlevler kümesinden oluşur. Uzak bilgisayar sistemlerini yöneten ve izleyen araçlar ve kitaplıklar geliştirmenize olanak tanır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

API aşağıdaki işlevleri içerir:

| İşlev | Açıklama |
|---------|---------|
| [BeginEnumeration işlevi](beginenumeration.md) | Numaralandırıcı, WMI nesne özellikleri numaralandırmasının başlangıcına sıfırlanır. |
| [BeginMethodEnumeration işlevi](beginmethodenumeration.md) |  Bir nesne için kullanılabilen yöntemlerin bir listesini başlatır. |
| [BlessIWbemServices işlevi](blessiwbemservices.md) | Kullanıcı kimlik bilgilerinin belirtilen bir IWbemServices sınıfına erişime izin verip vermediğini belirtir. |
| [BlessIWbemServicesObject işlevi](blessiwbemservicesobject.md) | Kullanıcı kimlik bilgilerinin belirtilen ıwbem hizmeti nesnesine erişime izin verip vermediğini belirtir. |
| [Clone işlevi](clone.md) | Geçerli nesnenin tamamen kopyası olan yeni bir nesne döndürür. |
| [CloneEnumWbemClassObject işlevi](cloneenumwbemclassobject.md) | Bir Numaralandırıcının mantıksal bir kopyasını oluşturur ve geçerli konumunu bir numaralandırıcıda korur. |
| [CompareTo işlevi](compareto.md) | Bir nesneyi başka bir Windows Yönetim nesnesiyle karşılaştırır. |
| [ConnectServerWmi işlevi](connectserverwmi.md) | Belirtilen bir bilgisayardaki WMI ad alanına DCOM aracılığıyla bir bağlantı oluşturur. |
| [CreateClassEnumWmi işlevi](createclassenumwmi.md) | Belirtilen seçim ölçütlerini karşılayan tüm sınıflar için bir Numaralandırıcı döndürür. |
| [Createınstanceenumwmi işlevi](createinstanceenumwmi.md) | Belirtilen seçim ölçütlerine uyan belirli bir sınıfın örneklerini döndüren bir Numaralandırıcı döndürür. |
| [Delete işlevi](delete.md) | Belirtilen bir özelliği bir sınıf tanımından ve tüm niteleyicilerine siler. |
| [DeleteMethod işlevi](deletemethod.md) | Belirtilen bir yöntemi CıM sınıf tanımından siler. |
| [EndEnumeration işlevi](endenumeration.md) | Bir numaralandırma dizisini sonlandırır. |
| [EndMethodEnumeration işlevi](endmethodenumeration.md) | [Beginmethodenumeration işlevini](beginmethodenumeration.md)çağırarak başlatılan bir numaralandırma dizisini sonlandırır. |
| [ExecNotificationQueryWmi işlevi](execnotificationquerywmi.md) | Olayları almak için bir sorgu yürütür. |
| [ExecQueryWmi işlevi](execquerywmi.md) | Nesneleri almak için bir sorgu yürütür. |
| [FormatFromRawValue işlevi](formatfromrawvalue.md) | Biçim dönüştürmesi zaman tabanlıysa, bir ham performans verisi değerini belirtilen biçime veya iki ham performans verisi değerine dönüştürür. |
| [Get işlevi](get.md) | Varsa, belirtilen bir özellik değerini alır. |
| [GetCurrentApartmentType işlevi](getcurrentapartmenttype.md) | Çağıranın yürütüldüğü grup türünü alır. |
| [GetDemultiplexedStub işlevi](getdemultiplexedstub.md) | Bir istemciye Windows yönetiminden zaman uyumsuz çağrılar alma konusunda yardımcı olmak için bir nesne iletici havuzu oluşturur. |
| [GetErrorInfo işlevi](geterrorinfo.md) | Önceki işlev çağrısından hata bilgilerini alır. |
| [GetMethod işlevi](getmethod.md) | Belirtilen yöntem hakkında bilgi alır. |
| [GetMethodOrigin işlevi](getmethodorigin.md) | Bir yöntemin bildirildiği sınıfı belirler. |
| [GetMethodQualifierSet işlevi](getmethodqualifierset.md) | Belirli bir yöntem için niteleyici kümesini alır. |
| [GetNames işlevi](getnames.md) | Bir nesnenin özelliklerinin bir alt kümesini ya da tümünü alır. |
| [GetObjectText işlevi](getobjecttext.md) | MOF sözdiziminde bir nesnenin metinsel işlemesini döndürür. |
| [GetPropertyHandle işlevi](getpropertyhandle.md) | Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür. |
| [GetPropertyOrigin işlevi](getpropertyorigin.md) | Özelliğin bildirildiği sınıfı belirler. |
| [GetPropertyQualifierSet işlevi](getpropertyqualifierset.md) | Belirli bir özellik için niteleyici kümesini alır.  |
| [GetQualifierSet işlevi](getqualifierset.md) | Bir sınıf örneği veya sınıf tanımı için niteleyici kümesini alır. |
| [Inhersfrom işlevi](inheritsfrom.md) | Geçerli sınıfın veya örneğin belirtilen bir üst sınıftan türeip türetilmediğini belirler. |
| [Initialize işlevi](initialize.md) | WMI başlatması gerçekleştirir. |
| [Next işlevi](next.md) | Bir Numaralandırmadaki bir sonraki özelliği alır. |
| [NextMethod işlevi](nextmethod.md) | Bir Numaralandırmadaki bir sonraki yöntemi alır. |
| [Put işlevi](put.md) | Adlandırılmış bir özelliği yeni bir değere ayarlar. |
| [PutClassWmi işlevi](putclasswmi.md) | Yeni bir sınıf oluşturur veya var olan bir sınıfı güncelleştirir. |
| [Putınstancewmi işlevi](putinstancewmi.md) | Var olan bir sınıfın örneğini oluşturur veya güncelleştirir. Örnek, WMI deposuna yazılır. |
| [PutMethod işlevi](putmethod.md) | Bir yöntem oluşturur. |
| [QualifierSet_BeginEnumeration işlevi](qualifierset-beginenumeration.md) | Bir nesnenin niteleyicilerinin bir Numaralandırıcı, numaralandırmanın başlangıcına sıfırlanır. |
| [QualifierSet_Delete işlevi](qualifierset-delete.md) | Belirtilen niteleyiciyi ada göre siler.  |
| [QualifierSet_EndEnumeration işlevi](qualifierset-endenumeration.md) | `QualifierSet_BeginEnumeration` işlevi çağrısıyla başlatılan numaralandırmayı sonlandırır. |
| [QualifierSet_Get işlevi](qualifierset-get.md) | Belirtilen adlandırılmış niteleyiciyi alır.  |
| [QualifierSet_GetNames işlevi](qualifierset-getnames.md) | Geçerli nesne veya özellikten kullanılabilen tüm niteleyicilerin veya belirtilen niteleyicilerin adlarını alır. |
| [QualifierSet_Next işlevi](qualifierset-next.md) | Bir [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi çağrısıyla başlatılan bir Numaralandırmadaki bir sonraki niteleyiciyi alır. |
| [QualifierSet_Put işlevi](qualifierset-put.md) | Adlandırılmış niteleyiciyi ve değeri yazar. |
| [ResetSecurity işlevi](resetsecurity.md) | Sağlanan kimliğe bürünme belirtecini geçerli iş parçacığına atar. |
| [SetSecurity işlevi](setsecurity.md) | Geçerli iş parçacığıyla ilişkili kimliğe bürünme belirtecini alır. |
| [SpawnDerivedClass işlevi](spawnderivedclass.md) | Belirtilen nesneden yeni türetilmiş sınıf nesnesi oluşturur. |
| [SpawnInstance işlevi](spawninstance.md) | Bir sınıfın yeni bir örneğini oluşturur. |
| [VerifyClient işlevi](verifyclientkey.md) | İstemci anahtarının doğru güvenliğe sahip olmasını sağlar. |
| [WritePropertyValue işlevi](writepropertyvalue.md) | Bir özellik tanıtıcısı tarafından tanımlanan bir özelliğe belirtilen sayıda bayt yazar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen API başvurusu](../index.md)
