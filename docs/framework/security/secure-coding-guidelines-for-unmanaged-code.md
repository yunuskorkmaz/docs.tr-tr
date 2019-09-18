---
title: Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 867157b329218b79c8cc1255b2158bbe83666531
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045363"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri
Bazı kitaplık kodunun yönetilmeyen koda (örneğin, Win32 gibi yerel kod API 'Leri) çağırması gerekir. Bu, yönetilen kod için güvenlik çevresi dışında bir süre içinde olduğu için dikkat gerektiren nedenlerle gereklidir. Kodunuz güvenlik tarafsız ise, hem kodunuz hem de bunu çağıran tüm kodlar yönetilmeyen kod iznine sahip olmalıdır (<xref:System.Security.Permissions.SecurityPermission> belirtilen <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrağıyla birlikte).  
  
 Ancak, çağıranın bu tür güçlü izinlere sahip olması genellikle mantıklı değildir. Bu gibi durumlarda, güvenilen kodunuz, [sarmalayıcı kodunu güvenli hale](../misc/securing-wrapper-code.md)getirmek için tanımlanan yönetilen sarmalayıcıya veya kitaplık koduna benzer şekilde, arasında hareket edebilir. Temel alınan yönetilmeyen kod işlevselliği tamamen güvende ise, doğrudan açığa çıkabilir; Aksi takdirde, önce uygun bir izin denetimi (istek) gereklidir.  
  
 Kodunuz yönetilmeyen koda çağırdığında ancak çağıranlarınızın yönetilmeyen koda erişim izni olmasını gerektirmek istiyorsanız, doğru onay yapmanız gerekir. Bir onaylama işlemi, kariyerinize yol gösterecek şekilde blok yapar. Bu işlemde bir güvenlik deliği oluşturmamaya dikkat etmeniz gerekir. Bu, genellikle çağıranlarınızın uygun bir iznini talep etmeniz ve yönetilmeyen kod kullanarak yalnızca bu iznin izin verdiği ve daha fazla izin verdiğini yapmanız gerektiği anlamına gelir. Bazı durumlarda (örneğin, bir gün saati), yönetilmeyen kod herhangi bir güvenlik denetimi olmadan çağıranlara doğrudan sunulabilir. Herhangi bir durumda, onay veren tüm kodlar güvenlik için sorumluluk almalıdır.  
  
 Yerel koda bir kod yolu sağlayan herhangi bir yönetilen kod, kötü amaçlı kod için olası bir hedeftir, bu nedenle hangi yönetilmeyen kodun güvenli bir şekilde kullanılabileceğini ve kullanılması gereken çok dikkatli olması gerekir. Genellikle, yönetilmeyen kod asla kısmen güvenilen çağıranlar için hiçbir şekilde doğrudan gösterilmemelidir. Kısmen güvenilen kod tarafından çağrılabilir olan kitaplıklarda yönetilmeyen kod kullanımı güvenliğini değerlendirmek için başlıca iki önemli noktalar vardır:  
  
- **İşlevselliği**. Yönetilmeyen API, çağıranların potansiyel olarak tehlikeli işlemler gerçekleştirmesine izin verilmeyen işlevler sağlıyor mu? Kod erişim güvenliği, kaynaklara erişimi zorlamak için izinleri kullanır, bu nedenle API 'nin dosyaları, Kullanıcı arabirimini veya iş parçacığı kullanıp kullanmadığını veya korunan bilgileri kullanıp kullanmadığını düşünün. Varsa, yönetilen kod sarmalama, girilmeye izin vermeden önce gerekli izinleri talep etmelidir. Ayrıca, bir izin tarafından korunmadığında, bellek erişiminin katı tür güvenliği ile sınırlandırımış olması gerekir.  
  
- **Parametre denetimi**. Yaygın saldırı, yönetilmeyen kod API yöntemlerine sunulan beklenmedik parametreleri, bunların belirtim dışında çalışmasına neden olan bir girişimle geçirir. Aralık dışı dizin veya fark değerleri kullanılarak yapılan arabellek taşmaları, temel koddaki bir hatadan faydalanan her türlü parametre gibi bu tür bir saldırının yaygın bir örneğidir. Bu nedenle, kısmen güvenilen çağıranlar için yönetilmeyen kod API 'SI işlevsel güvenli olsa bile, yönetilen kod aynı zamanda, yönetilen bir kod tarafından kötü amaçlı koddan hiçbir istenmeyen çağrının olmamasını sağlamak kod sarmalayıcı katmanı.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>SuppressUnmanagedCodeSecurityAttribute Kullanma  
 Yönetilmeyen kodu ele almak ve ardından çağırmak için bir performans yönü vardır. Her bu çağrı için, güvenlik sistemi otomatik olarak yönetilmeyen kod iznini talep ediyor ve bu da yığın her seferinde izlenecek bir sonuç. Yönetilmeyen kodu onaylama ve anında çağrı yaparsanız yığın ilerleme durumunu anlamlı bir şekilde kullanabilirsiniz: Bu, onayı ve yönetilmeyen kod çağrınızdan oluşur.  
  
 Belirtilen <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> izin<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> ile talep <xref:System.Security.Permissions.SecurityPermission> edilen normal güvenlik denetimini devre dışı bırakmak için, çağrılan özel bir öznitelik yönetilmeyen kod giriş noktalarına uygulanabilir. Bu eylem, çalışma zamanı güvenlik denetimi olmadan yönetilmeyen koda açık bir kapılı olduğundan, her zaman çok dikkatli olunmalıdır. **SuppressUnmanagedCodeSecurityAttribute** uygulanmış olsa da, hemen çağıranın yönetilmeyen kodu çağırma iznine sahip olduğundan emin olmak için tam ZAMANıNDA (JIT) derlemede gerçekleşen tek seferlik bir güvenlik denetimi vardır.  
  
 **SuppressUnmanagedCodeSecurityAttribute**kullanırsanız aşağıdaki noktaları kontrol edin:  
  
- Yönetilmeyen kod giriş noktasını, kodunuzun dışından iç veya başka bir şekilde erişilemez yapın.  
  
- Yönetilmeyen koda yapılan herhangi bir çağrı olası bir güvenlik deliği. Kodunuzun, kötü amaçlı kodun yönetilmeyen koda dolaylı olarak çağırması ve güvenlik denetiminden kaçınmak için bir portal olmadığından emin olun. Uygunsa talep izinleri.  
  
- Aşağıdaki bölümde açıklandığı gibi, yönetilmeyen kod için tehlikeli bir yol oluştururken açıkça tanımlamak üzere bir adlandırma kuralı kullanın.  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Yönetilmeyen kod yöntemleri için adlandırma kuralı  
 Yönetilmeyen kod yöntemlerini adlandırmak için kullanışlı ve son derece önerilen bir kural oluşturulmuştur. Tüm yönetilmeyen kod yöntemleri üç kategoride ayrılır: **güvenli**, **Yerel**ve **güvenli olmayan**. Bu anahtar sözcükler, çeşitli yönetilmeyen kod giriş noktası türlerinin tanımlandığı sınıf adı olarak kullanılabilir. Kaynak kodunda, bu anahtar sözcüklerin `Safe.GetTimeOfDay`, `Native.Xyz`, veya `Unsafe.DangerousAPI`gibi sınıf adına eklenmesi gerekir. Bu anahtar sözcüklerin her biri, aşağıdaki tabloda açıklandığı gibi, bu sınıfı kullanan geliştiriciler için yararlı güvenlik bilgileri sağlar.  
  
|Anahtar sözcüğü|Güvenlik konuları|  
|-------------|-----------------------------|  
|**güven**|Herhangi bir kod için, hatta kötü amaçlı kod, çağırmak için tamamen zararsız. , Diğer yönetilen kod gibi kullanılabilir. Örneğin, günün saatini alan bir işlev genellikle güvenlidir.|  
|**Yerel**|Güvenlikle bağımsız; diğer bir deyişle, yönetilmeyen kod iznini çağıran yönetilmeyen kod. Güvenlik denetlenir ve bu da yetkisiz bir çağrıyı sonlandırır.|  
|**unsafe**|Güvenliği gizlenen, potansiyel olarak tehlikeli, yönetilmeyen kod giriş noktası. Geliştiriciler, bu tür yönetilmeyen kodu kullanırken en büyük dikkatli bir güvenlik açığını engellemek için diğer korumaların yerinde olduğundan emin olmalıdır. Bu anahtar sözcük güvenlik sistemini geçersiz kıldığından, geliştiricilerin sorumlu olması gerekir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
