---
title: Tanımlayıcı adlı derlemeler oluşturma ve kullanma
ms.date: 08/19/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
ms.openlocfilehash: 18a0b7d657290835a34c705513d0d7a4ccbfc61c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75738688"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tanımlayıcı adlı derlemeler oluşturma ve kullanma

Güçlü bir ad, derlemenin kimliğinden oluşur— basit metin adı, sürüm numarası ve kültür bilgileri (sağlanmışsa)—ortak anahtar ve dijital imza. İlgili özel anahtar kullanılarak bir derleme dosyasından oluşturulur. (Derleme dosyası, derlemeyi oluşturan tüm dosyaların adlarını ve işlerini içeren derleme bildirimini içerir.)

> [!WARNING]
> Güvenlik için güçlü isimlere güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

Güçlü adlandırılmış derleme yalnızca diğer güçlü adlandırılmış derlemelerden türleri kullanabilir. Aksi takdirde, güçlü adlı derlemenin bütünlüğü tehlikeye girer.

> [!NOTE]
> .NET Core güçlü adlandırılmış derlemeleri desteklese ve .NET Core kitaplığındaki tüm derlemeler imzalanmış olsa da, üçüncü taraf derlemelerin çoğunluğugüçlü adlara ihtiyaç duymaz. Daha fazla bilgi için GitHub'da [Güçlü Ad İmzalama'ya](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) bakın.

## <a name="strong-name-scenario"></a>Güçlü ad senaryosu

Aşağıdaki senaryo, güçlü bir ada sahip bir derlemeyi imzalama ve daha sonra bu ada başvurma işlemini özetleyin.

1. Derleme A, aşağıdaki yöntemlerden biri kullanılarak güçlü bir adla oluşturulur:

    - Visual Studio gibi güçlü adlar oluşturmayı destekleyen bir geliştirme ortamı kullanma.

    - [Güçlü Ad aracını (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) kullanarak bir şifreleme anahtar çifti oluşturma ve bu anahtar çiftini bir komut satırı derleyicisi veya [Derleme Bağlayıcısı (Al.exe)](../../framework/tools/al-exe-assembly-linker.md)kullanarak derlemeye atama. Windows SDK hem Sn.exe hem de Al.exe sağlar.

2. Geliştirme ortamı veya araç, derlemenin bildirimini içeren dosyanın karmasını geliştiricinin özel anahtarıyla işaretler. Bu dijital imza, Assembly A'nın bildirimini içeren taşınabilir yürütülebilir (PE) dosyasında depolanır.

3. B Meclisi A Meclisi'nin tüketicisidir. B Meclisi'nin manifestosunun başvuru bölümü, Meclis A'nın ortak anahtarını temsil eden bir belirteç içerir. Belirteç, tam ortak anahtarın bir bölümüdür ve anahtar dan çok yer kazanmak için kullanılır.

4. Ortak dil çalışma süresi, derleme genel derleme önbelleğine yerleştirildiğinde güçlü ad imzasını doğrular. Çalışma zamanında güçlü bir ada göre bağlandığında, ortak dil çalışma süresi, B Derlemesi'nin manifestosunda depolanan anahtarı, A Derlemesi için güçlü bir ad oluşturmak için kullanılan anahtarla karşılaştırır. .NET Framework güvenlik denetimleri geçerse ve bağlama başarılı olursa, B Derlemesi A'nın bitlerinin değiştirilmediğini ve bu bitlerin aslında A Derlemesi geliştiricilerinden geldiğinin bir garantisi vardır.

> [!NOTE]
> Bu senaryo güven sorunlarını ele almaz. Derlemeler, güçlü bir ada ek olarak tam Microsoft Authenticode imzaları taşıyabilir. Authenticode imzaları güven oluşturan bir sertifika içerir. Güçlü adların bu şekilde imzalanacak kod gerektirmediğini unutmayın. Güçlü adlar yalnızca benzersiz bir kimlik sağlar.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Güvenilir derlemelerin imza doğrulamasını atlama

.NET Framework 3.5 Service Pack 1'den başlayarak, bir derleme `MyComputer` bölge için varsayılan uygulama etki alanı gibi tam güven uygulama etki alanına yüklendiğinde güçlü ad imzaları doğrulanmaz. Buna güçlü ad bypass özelliği denir. Tam güven ortamında, imzaları <xref:System.Security.Permissions.StrongNameIdentityPermission> ne olursa olsun imzalı, tam güven derlemeleri için her zaman başarılı talepler. Güçlü ad atlama özelliği, bu durumda tam güven derlemelerinin güçlü ad imza doğrulamasının gereksiz ek yükünü önleyerek derlemelerin daha hızlı yüklenmesini sağlar.

Baypas özelliği, güçlü bir adla imzalanmış ve aşağıdaki özelliklere sahip tüm derlemeler için geçerlidir:

- Kanıt olmadan <xref:System.Security.Policy.StrongName> tamamen güvenilirdir (örneğin, bölge kanıtları vardır). `MyComputer`

- Tamamen güvenilir bir <xref:System.AppDomain>içine yüklendi .

- Bu özelliği altında <xref:System.AppDomainSetup.ApplicationBase%2A> bir konumdan <xref:System.AppDomain>yüklenir.

- Gecikme imzalı değil.

Bu özellik tek tek uygulamalar veya bir bilgisayar için devre dışı alınabilir. [Bkz. Nasıl Yapılır: Güçlü ad atlama özelliğini devre dışı sayıl.](disable-strong-name-bypass-feature.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapilir: Genel-özel anahtar çifti oluşturma](create-public-private-key-pair.md)|Derlemeyi imzalamak için şifreleme anahtar çiftinin nasıl oluşturulduğunu açıklar.|
|[Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama](sign-strong-name.md)|Güçlü adlandırılmış bir derlemenin nasıl oluşturulabildiğini açıklar.|
|[Geliştirilmiş güçlü adlandırma](enhanced-strong-naming.md)|.NET Framework 4.5'teki güçlü adlara yapılan geliştirmeleri açıklar.|
|[Nasıl yapılsın: Güçlü bir derlemeye başvuru](reference-strong-named.md)|Derleme zamanında veya çalışma zamanında, güçlü adlandırılmış bir derlemedeki türlere veya kaynaklara nasıl başvurulmayı açıklar.|
|[Nasıl yapılır: Güçlü ad atlama özelliğini devre dışı](disable-strong-name-bypass-feature.md)|Güçlü ad imzalarının doğrulanmasını atlayan özelliğin nasıl devre dışı kalınır olduğunu açıklar. Bu özellik tüm veya belirli uygulamalar için devre dışı alınabilir.|
|[Derleme oluşturma](create.md)|Tek dosyalı ve çok dosyalı derlemelere genel bakış sağlar.|
|[Visual Studio'da montaj imzalamayı nasıl geciktirir?](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Derleme oluşturulduktan sonra güçlü bir ada sahip bir derlemenin nasıl imzalandığını açıklar.|
|[Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)|.NET Framework'de yer alan ve güçlü adlara sahip derlemeler oluşturmaya yardımcı olan aracı açıklar. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.|
|[Al.exe (Montaj bağlayıcısı)](../../framework/tools/al-exe-assembly-linker.md)|.NET Framework'de yer alan ve modüllerden veya kaynak dosyalarından derleme bildirimi olan bir dosya oluşturan aracı açıklar.|
