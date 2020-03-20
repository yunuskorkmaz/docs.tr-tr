---
title: WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)
description: WMI ve performans sayacı bilgileri için .NET Framework yönetilmeyen API'yi özetler.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127416"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Yönetim Araçları (WMI) ve Performans Sayaçları (Yönetilmeyen API Başvurusu)

.NET Framework WMI ve Performans Sayaçları yönetilmeyen API, [ana Windows Yönetimi Enstrümantasyon API'sine](/windows/desktop/WmiSdk/com-api-for-wmi)çağrıları kaydıran bir dizi işlevden oluşur. Uzak bilgisayar sistemlerini yöneten ve izleyen araçlar ve kütüphaneler geliştirmenize olanak tanır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

API aşağıdaki işlevleri içerir:

| İşlev | Açıklama |
|---------|---------|
| [BeginEnumeration işlevi](beginenumeration.md) | Numaralandırıcıyı WMI nesne özelliklerinin numaralandırmasının başına sıfırlar. |
| [BeginMethodEnumeration işlevi](beginmethodenumeration.md) |  Bir nesne için kullanılabilir yöntemlerin numaralandırmasını başlatın. |
| [BlessIWbemServices işlevi](blessiwbemservices.md) | Kullanıcı kimlik bilgilerinin belirli bir IWbemServices sınıfına erişime izin verip vermediğini gösterir. |
| [BlessIWbemServicesObject işlevi](blessiwbemservicesobject.md) | Kullanıcı kimlik bilgilerinin belirtilen bir IWbem hizmet nesnesine erişime izin verip vermediğini gösterir. |
| [Clone işlevi](clone.md) | Geçerli nesnenin tam bir klonu olan yeni bir nesne döndürür. |
| [CloneEnumWbemClassObject işlevi](cloneenumwbemclassobject.md) | Numaralandırmada geçerli konumunu koruyarak numaralandırmanın mantıksal bir kopyasını yapar. |
| [CompareTo işlevi](compareto.md) | Bir nesneyi başka bir Windows yönetim nesnesi ile karşılaştırır. |
| [ConnectServerWmi fonksiyonu](connectserverwmi.md) | DCOM üzerinden belirli bir bilgisayardaki WMI ad alanına bağlantı oluşturur. |
| [ClassEnumWmi işlevini oluştur](createclassenumwmi.md) | Belirtilen seçim ölçütlerini karşılayan tüm sınıflar için bir sayısallaştırıcı döndürür. |
| [CreateInstanceEnumWmi fonksiyonu](createinstanceenumwmi.md) | Belirtilen seçim ölçütlerini karşılayan belirli bir sınıfın örneklerini döndüren bir sayısallaştırıcı döndürür. |
| [Delete işlevi](delete.md) | Belirli bir özelliği sınıf tanımından ve tüm niteleyicilerinden siler. |
| [DeleteMethod işlevi](deletemethod.md) | Cim sınıf tanımından belirtilen yöntemi siler. |
| [EndEnumeration işlevi](endenumeration.md) | Numaralandırma sırasını sonlandırır. |
| [EndMethodEnumeration işlevi](endmethodenumeration.md) | [BeginMethodEnumeration işlevini](beginmethodenumeration.md)çağırarak başlatılan numaralandırma dizisini sonlandırır. |
| [ExecNotificationQueryWmi işlevi](execnotificationquerywmi.md) | Olayları almak için bir sorgu yürütür. |
| [ExecQueryWmi işlevi](execquerywmi.md) | Nesneleri almak için bir sorgu yürütür. |
| [FormatFromRawValue işlevi](formatfromrawvalue.md) | Biçim dönüştürme zamana dayalıysa, bir ham performans veri değerini belirtilen biçime veya iki ham performans veri değerine dönüştürür. |
| [Get işlevi](get.md) | Varsa belirtilen bir özellik değerini alır. |
| [GetCurrentApartmentType fonksiyonu](getcurrentapartmenttype.md) | Arayanın yürütüldettiği daire türünü alır. |
| [GetDemultiplexedStub fonksiyonu](getdemultiplexedstub.md) | Windows Yönetimi'nden eşzamanlı çağrılar almada istemciye yardımcı olmak için bir nesne ilemör lavabosu oluşturur. |
| [GetErrorInfo fonksiyonu](geterrorinfo.md) | Önceki işlev çağrısından hata bilgilerini alır. |
| [GetMethod işlevi](getmethod.md) | Belirtilen yöntem le ilgili bilgileri alır. |
| [GetMethodOrigin işlevi](getmethodorigin.md) | Yöntemin bildirildiği sınıfı belirler. |
| [GetMethodQualifierSet işlevi](getmethodqualifierset.md) | Belirli bir yöntem için niteleyici kümesini alır. |
| [GetNames işlevi](getnames.md) | Bir alt kümeyi veya nesnenin özelliklerinin tüm adlarını alır. |
| [GetObjectText işlevi](getobjecttext.md) | MOF sözdiziminde bir nesnenin metinsel oluşturmasını döndürür. |
| [GetPropertyHandle işlevi](getpropertyhandle.md) | Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür. |
| [GetPropertyOrigin işlevi](getpropertyorigin.md) | Bir özelliğin beyan edildiği sınıfı belirler. |
| [GetPropertyQualifierSet fonksiyonu](getpropertyqualifierset.md) | Belirli bir özellik için niteleyici kümesini alır.  |
| [GetQualifierSet fonksiyonu](getqualifierset.md) | Bir sınıf örneği veya sınıf tanımı için niteleyici kümesini alır. |
| [DevralmalarFrom işlevi](inheritsfrom.md) | Geçerli sınıfın veya örneğin belirli bir üst sınıftan türetilip türedip türetilemeyeceğini belirler. |
| [İşlevbaşlatma](initialize.md) | WMI başlatma gerçekleştirir. |
| [Sonraki fonksiyon](next.md) | Bir sonraki özelliği numaralandırmada alır. |
| [NextMethod fonksiyonu](nextmethod.md) | Bir sonraki yöntemi numaralandırmada alır. |
| [Put fonksiyonu](put.md) | Adlandırılmış bir özelliği yeni bir değere ayarlar. |
| [PutClassWmi fonksiyonu](putclasswmi.md) | Yeni bir sınıf oluşturur veya varolan bir sınıfı güncelleştirir. |
| [PutInstanceWmi fonksiyonu](putinstancewmi.md) | Varolan bir sınıfın bir örneğini oluşturur veya güncelleştirir. Örnek WMI deposuna yazılır. |
| [PutMethod fonksiyonu](putmethod.md) | Bir yöntem oluşturur. |
| [QualifierSet_BeginEnumeration fonksiyonu](qualifierset-beginenumeration.md) | Bir nesnenin niteleyicisini numaralandırmanın başına sıfırlar. |
| [QualifierSet_Delete fonksiyonu](qualifierset-delete.md) | Belirtilen bir niteleyiciyi ada göre siler.  |
| [QualifierSet_EndEnumeration fonksiyonu](qualifierset-endenumeration.md) | İşlev için yapılan bir çağrıyla başlayan `QualifierSet_BeginEnumeration` numaralandırmayı sonlandırır. |
| [QualifierSet_Get fonksiyonu](qualifierset-get.md) | Belirtilen adlandırılmış niteleyiciyi alır.  |
| [QualifierSet_GetNames fonksiyonu](qualifierset-getnames.md) | Geçerli nesne veya özellikten kullanılabilen tüm niteleyicilerin veya belirli niteleyicilerin adlarını alır. |
| [QualifierSet_Next fonksiyonu](qualifierset-next.md) | [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevine yapılan bir çağrıyla başlayan bir numaralandırmada bir sonraki elemeyi alır. |
| [QualifierSet_Put fonksiyonu](qualifierset-put.md) | Adlandırılmış niteleyici ve değeri yazar. |
| [ResetSecurity işlevi](resetsecurity.md) | Verilen kimliğe bürünme belirteci belirteci geçerli iş parçacığına atar. |
| [SetSecurity işlevi](setsecurity.md) | Geçerli iş parçacığı ile ilişkili kimliğe bürünme belirteci alır. |
| [SpawnDerivedClass fonksiyonu](spawnderivedclass.md) | Belirtilen bir nesneden yeni türetilmiş bir sınıf nesnesi oluşturur. |
| [SpawnInstance fonksiyonu](spawninstance.md) | Sınıfın yeni bir örneğini oluşturur. |
| [VerifyClient işlevi](verifyclientkey.md) | İstemci anahtarının doğru güvenliğe sahip olmasını sağlar. |
| [WritePropertyValue fonksiyonu](writepropertyvalue.md) | Özellik tutamacı tarafından tanımlanan bir özelliğe belirli sayıda bayt yazar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen API başvurusu](../index.md)
