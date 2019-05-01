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
ms.openlocfilehash: 138713c4a1397369ea18792a3b2742389b107a6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951716"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri
Yönetilmeyen kod (örneğin, yerel kod API'leri, Win32 gibi) çağırmak bazı kitaplık kodu gerekiyor. Bu son yönetilen kod için güvenlik çevresi dışarıya gitme anlamına gelir çünkü dikkat gerekiyor. Tarafsız güvenlik kodunuz ise hem kodunuz hem de onu çağıran herhangi bir kod kod iznini yönetilmeyen gerekir (<xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> belirtilmiş işareti).  
  
 Ancak, genellikle, arayanın güçlü tür izinlere sahip olmasını mantıksız olur. Bu gibi durumlarda, güvenilen kod için yönetilen sarmalayıcı benzer aracılık olabilir veya kitaplık kodu açıklanan [sarmalayıcı kodunun güvenliğini sağlama](../../../docs/framework/misc/securing-wrapper-code.md). Temel alınan yönetilmeyen kod işlevselliğini tamamen güvenli olup olmadığını, doğrudan gösterilebilir; Aksi takdirde, uygun izne onay (isteğe bağlı) ilk gereklidir.  
  
 Kodunuzu yönetilmeyen koda çağıran ancak yönetilmeyen koda erişim iznine sahip çağrı yapanların gerektirecek şekilde istemiyorsanız, bu hak onay gerekir. Yığın ilerlemesi, kare onaylama engeller. Bu işlemde bir güvenlik açığı oluşturmayın dikkatli olmanız gerekir. Genellikle, bu, Arayanların, uygun bir izin talep ve ardından yalnızca ne izni verir ve artık gerçekleştirmek için yönetilmeyen kod kullanın anlamına gelir. Bazı durumlarda (örneğin, bir get günün saati işlevi) yönetilmeyen kod arayanlara tüm güvenlik denetimleri olmadan doğrudan sunulabilir. Her iki durumda da onaylar herhangi bir kod, güvenlik sorumluluğunu üstlenmelidir.  
  
 Yerel kod içine kod yolu sağlayan herhangi bir yönetilen kod için kötü amaçlı kod olası hedef olduğundan, hangi yönetilmeyen kod belirleme güvenli bir şekilde kullanılabilir ve son derece dikkatli olunmalıdır nasıl kullanılmalıdır gerektirir. Genellikle, yönetilmeyen koda hiçbir zaman doğrudan kısmen güvenilen arayanlara açılmamalıdır. Yönetilmeyen kod kısmen güvenilen kod tarafından çağrılabilir kitaplıkları kullanımda güvenliğini değerlendirme içinde iki birincil ilgili önemli noktalar vardır:  
  
- **İşlevsellik**. Yönetilmeyen API potansiyel olarak tehlikeli olabilecek işlemleri gerçekleştirmek bir çağırıcıya izin vermeyen bir işlevsellik sağlar mı? Kod erişimi güvenliği, kaynaklara erişim de uygular, böylece API dosyaları, bir kullanıcı arabirimi kullanıp kullanmadığını göz önünde bulundurun için izinleri kullanır veya iş parçacığı, veya bilgi korumalı olup olmadığını gösterir. Aşması durumunda, sarmalama yönetilen koda izin vermeden önce gerekli izinleri talep gerekir. Ayrıca, bir izin tarafından korunmayan olsa da bellek erişimi için katı tür güvenliği sýnýrlandýrýlmasýna gerekir.  
  
- **Parametre denetimi**. Yaygın bir saldırı geçişleri beklenmeyen parametreleri belirtimi dışında çalışmasına neden girişimi API yönetilmeyen kod yöntemleri açığa. Aralık dışı dizin kullanarak arabellek taşmasına neden veya arka plandaki kod bir hata yararlanabilir herhangi bir parametre olarak uzaklık değerleri bu tür saldırılar, yaygın bir örneği değil. Yönetilmeyen kod API (sonra gerekli taleplerini) kısmen güvenilen için işlevsel olarak güvenli olsa bile, bu nedenle, çağıranlar, yönetilen gerekir ayrıca olsak da istenmeyen çağrı kötü amaçlı koddan yönetilen kullanarak mümkün olduğundan emin olmak için onay parametresi geçerlilik kod kod sarmalayıcı katmanı.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>SuppressUnmanagedCodeSecurityAttribute Kullanma  
 Sunduğundan ve ardından yönetilmeyen kod çağırmak için bir performans en boy yoktur. Böyle her bir çağrı için güvenlik sistem otomatik olarak her zaman içinde bir yığın ilerlemesi kaynaklanan yönetilmeyen kod iznine ihtiyaç duyar. Assert ve hemen yönetilmeyen kod çağırmak, yığın ilerlemesi anlamsız olabilir:, onay ve yönetilmeyen kod aramanız oluşur.  
  
 Özel bir öznitelik adında <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> talepleri normal güvenlik denetimi devre dışı bırakmak için yönetilmeyen kod giriş noktaları için uygulanabilir <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> belirtilen izni. Son derece dikkatli olun, her zaman bu eylem, hiçbir çalışma zamanı güvenlik ile yönetilmeyen koda açık bir kapı oluşturduğundan, böylece denetlerken atılmalıdır. Not edilmesi gereken olsa da, **SuppressUnmanagedCodeSecurityAttribute** uygulanan, just-in-time (JIT) derleme şu anki çağırıcı çağırma izni olduğundan emin olmak için gerçekleşen tek seferlik güvenlik denetimi yok yönetilmeyen kod.  
  
 Kullanırsanız **SuppressUnmanagedCodeSecurityAttribute**, şu noktaları kontrol edin:  
  
- Yönetilmeyen kod girişi noktası iç ya da aksi takdirde, kodunuz dışında erişilemez olun.  
  
- Tüm çağrıların yönetilmeyen koda olası bir güvenlik açığı var. Kodunuzu dolaylı olarak yönetilmeyen koda çağrı ve güvenlik denetimi önlemek için kötü amaçlı kod için bir portal olmadığından emin olun. Uygun izinleri talep.  
  
- Aşağıdaki bölümde açıklandığı gibi yönetilmeyen koda tehlikeli yol oluştururken açıkça tanımlamak için bir adlandırma kuralı kullanmak...  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Yönetilmeyen kod yöntemleri için adlandırma kuralı  
 Yönetilmeyen kod yöntemleri adlandırmak için kullanışlı ve yüksek oranda önerilen kuralı kuruldu. Tüm yönetilmeyen kod yöntemleri üç kategoriye ayrılır: **güvenli**, **yerel**, ve **güvenli**. Bu anahtar sözcükler çeşitli giriş noktaları yönetilmeyen kod içinde tanımlanmış sınıf adları kullanılabilir. Kaynak kodunda bu anahtar sözcükler sınıf adı olarak eklenmesi gereken `Safe.GetTimeOfDay`, `Native.Xyz`, veya `Unsafe.DangerousAPI`, örneğin. Aşağıdaki tabloda açıklandığı gibi her bu anahtar sözcüklerden biri bu sınıfı kullanan geliştiriciler için yararlı bir güvenlik bilgileri sağlar.  
  
|Anahtar sözcüğü|Güvenlik konuları|  
|-------------|-----------------------------|  
|**Güvenli**|Tamamen herhangi kod için çağrılacak bile kötü amaçlı kod zararsız. Yalnızca diğer yönetilen kod gibi kullanılabilir. Örneğin, günün saatini alır bir işlev genellikle güvenlidir.|  
|**Yerel**|Güvenlik-nötr; diğer bir deyişle, gerektiren yönetilmeyen kod çağırmak için kod iznini yönetilmeyen. Güvenlik, yetkisiz bir çağıranın vermemeye denetlenir.|  
|**unsafe**|Giriş noktasıyla gizlenen güvenlik tehlikeli yönetilmeyen kod. Geliştiricilerin en dikkat gibi yönetilmeyen kod kullanarak başka bir güvenlik açığını önlemek için korumaların emin emin kullanması gerekir. Bu anahtar sözcük güvenlik sistemi geçersiz kılar. geliştiriciler sorumlu olması gerekir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
