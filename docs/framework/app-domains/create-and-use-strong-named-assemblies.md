---
title: Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma
ms.date: 08/01/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dcdf6a88b12d12e67056657fd532dfa28c40299
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566816"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tanımlayıcı adlı derlemeler oluşturma ve kullanma

Tanımlayıcı ad, derleme kimliğinden (basit metin adı, sürüm numarası ve kültür bilgileri (sağlanmışsa) ve bir ortak anahtar ve dijital imza ile oluşur. Karşılık gelen özel anahtar kullanılarak derleme dosyasından oluşturulur. (Derleme dosyası, derlemeyi oluşturan tüm dosyaların adlarını ve karmalarını içeren derleme bildirimini içerir.)

> [!WARNING]
> Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir. Aksi takdirde, tanımlayıcı adlı derlemenin bütünlüğü tehlikeye girebilir.

## <a name="strong-name-scenario"></a>Tanımlayıcı ad senaryosu

Aşağıdaki senaryo, bir derlemeyi güçlü bir adla imzalama ve daha sonra bu ada göre başvuruda bulunma sürecini özetler.

1. Derleme A, aşağıdaki yöntemlerden biri kullanılarak bir tanımlayıcı ad ile oluşturulur:

    - Visual Studio gibi güçlü adlar oluşturmayı destekleyen bir geliştirme ortamı kullanma.

    - Bir komut satırı derleyicisi veya [derleme Bağlayıcısı (al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)kullanarak, [tanımlayıcı ad Aracı (sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) kullanarak bir şifreleme anahtarı çifti oluşturma ve bu anahtar çiftini derlemeye atama. Windows SDK hem sn. exe hem de al. exe sağlar.

2. Geliştirme ortamı veya aracı, geliştiricinin özel anahtarıyla derlemenin bildirimini içeren dosyanın karmasını imzalar. Bu dijital imza, derleme A 'nın bildirimini içeren taşınabilir çalıştırılabilir (PE) dosyasında depolanır.

3. Derleme B, A derlemesi tüketicisidir. Derleme B 'nin bildiriminin başvuru bölümü, derleme A 'nın ortak anahtarını temsil eden bir belirteç içerir. Belirteç, tam ortak anahtarın bir bölümüdür ve alan kazanmak için anahtarın kendisi yerine kullanılır.

4. Ortak dil çalışma zamanı, derleme genel derleme önbelleğine yerleştirildiğinde tanımlayıcı ad imzasını doğrular. Çalışma zamanında tanımlayıcı ada göre bağlamada ortak dil çalışma zamanı, derleme B 'nin bildiriminde depolanan anahtarı, derleme A için tanımlayıcı ad oluşturmak için kullanılan anahtarla karşılaştırır. .NET Framework güvenlik denetimi başarılı olursa ve bağlama başarılı olursa, derleme B, derleme A 'nın bitleri kurcalanmayan ve bu bitlerin aslında A derlemesi geliştiricilerinden geldiği garantisi vardır.

> [!NOTE]
> Bu senaryo güven sorunlarına yönelik değildir. Derlemeler, güçlü bir ada ek olarak tam Microsoft Authenticode imzalarını taşıyabilir. Authenticode imzaları, güven kuran bir sertifika içerir. Tanımlayıcı adların kodun bu şekilde imzalanmasını gerektirmediğini unutmayın. Tanımlayıcı adlar yalnızca benzersiz bir kimlik sağlar.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Güvenilen derlemelerin imza doğrulamasını atla

.NET Framework 3,5 Service Pack 1 ' den itibaren, bir derleme bir tam güvenli uygulama etki alanına yüklendiğinde, `MyComputer` bölgenin varsayılan uygulama etki alanı gibi tanımlayıcı ad imzaları doğrulanmaz. Bu, tanımlayıcı ad atlama özelliği olarak adlandırılır. Tam güven ortamında, <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalarından bağımsız olarak imzalı, tam güvenle derlemeler için her zaman başarılı olur. Güçlü ad atlama özelliği, bu durumda derlemelerin daha hızlı yüklenmesine izin vermek için tam güven derlemelerinin tanımlayıcı ad imzası doğrulamasının gereksiz ek yükünü önler.

Atlama özelliği, bir tanımlayıcı ad ile imzalanmış ve aşağıdaki özelliklere sahip olan her derleme için geçerlidir:

- Kanıt olmadan <xref:System.Security.Policy.StrongName> tamamen güvenilir (örneğin, bölge kanıtları vardır `MyComputer` ).

- Tam güvenilir <xref:System.AppDomain>bir şekilde yüklendi.

- <xref:System.AppDomainSetup.ApplicationBase%2A> Özelliği altında<xref:System.AppDomain>bir konumdan yüklendi.

- Gecikmeli imza değildir.

Bu özellik ayrı uygulamalar veya bir bilgisayar için devre dışı bırakılabilir. Bkz [. nasıl yapılır: Tanımlayıcı adı atlama özelliğini](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)devre dışı bırakın.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Ortak özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Bir derlemeyi imzalamak için bir şifreleme anahtarı çiftinin nasıl oluşturulacağını açıklar.|
|[Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Tanımlayıcı adlı derlemenin nasıl oluşturulacağını açıklar.|
|[Gelişmiş Kesin Adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md)|4,5 .NET Framework güçlü adlarla ilgili geliştirmeleri açıklar.|
|[Nasıl yapılır: Tanımlayıcı adlı bir derlemeye başvuru](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Derleme zamanında veya çalışma zamanında tanımlayıcı adlı bir derlemede türlerin veya kaynakların nasıl başvurululacağını açıklar.|
|[Nasıl yapılır: Tanımlayıcı adı atlama özelliğini devre dışı bırakma](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Tanımlayıcı ad imzalarının doğrulanmasını atlayan özelliğin nasıl devre dışı bırakılacağını açıklar. Bu özellik tüm veya belirli uygulamalar için devre dışı bırakılabilir.|
|[Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)|Tek dosyalı ve çoklu dosya Derlemeleriyle genel bir bakış sağlar.|
|[Visual Studio 'da bir derlemeyi IMZALAMAYı geciktirme](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Derleme oluşturulduktan sonra bir derlemeyi güçlü bir adla nasıl imzalayabileceğinizi açıklar.|
|[Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Güçlü adlara sahip derlemeler oluşturulmasına yardımcı olan .NET Framework dahil olan aracı açıklar. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.|
|[Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Modüller veya kaynak dosyalarından derleme bildirimine sahip bir dosya üreten .NET Framework dahil olan aracı açıklar.|
