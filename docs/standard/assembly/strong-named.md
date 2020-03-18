---
title: Tanımlayıcı adlandırılmış derlemeler
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
ms.openlocfilehash: 12b8df3195b2708e4556d4f8065227054db9eb14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711577"
---
# <a name="strong-named-assemblies"></a>Tanımlayıcı adlandırılmış derlemeler

Derlemeyi güçlü adlandırma, derleme için benzersiz bir kimlik oluşturur ve derleme çakışmalarını önleyebilir.

## <a name="what-makes-a-strong-named-assembly"></a>Güçlü bir derleme yi yapan nedir?

Güçlü bir adlandırılmış derleme, derleme ile dağıtılan ortak anahtara karşılık gelen özel anahtar ve derlemenin kendisi kullanılarak oluşturulur. Derleme, derlemeyi oluşturan tüm dosyaların adlarını ve işlerini içeren derleme bildirimini içerir. Aynı güçlü ada sahip derlemeler aynı olmalıdır.

Visual Studio veya komut satırı aracını kullanarak derlemeleri güçlü adlandırabilirsiniz. Daha fazla bilgi için [bkz: Güçlü bir ad](sign-strong-name.md) veya [Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)ile bir derleme imzalayın.

Güçlü adlandırılmış bir derleme oluşturulduğunda, derlemenin basit metin adını, sürüm numarasını, isteğe bağlı kültür bilgilerini, dijital imzayı ve imzalamak için kullanılan özel anahtara karşılık gelen ortak anahtarı içerir.

> [!WARNING]
> Güvenlik için güçlü isimlere güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

## <a name="why-strong-name-your-assemblies"></a>Neden meclislerinize sert bir isim veremin?

Güçlü adlandırılmış bir derlemeye başvururken, sürüm ve adlandırma koruması gibi belirli avantajlar bekleyebilirsiniz. .NET Framework'de, bazı senaryoları etkinleştirmek için gereken genel derleme önbelleğine güçlü adlandırılmış derlemeler yüklenebilir.

Güçlü adlı derlemeler aşağıdaki senaryolarda yararlıdır:

- Derlemelerinizin güçlü adlandırılmış derlemeler tarafından başvurulmasını sağlamak veya diğer `friend` güçlü adlandırılmış derlemelerden derlemelerinize erişim sağlamak istiyorsunuz.

- Bir uygulamanın aynı derlemenin farklı sürümlerine erişmesi gerekir. Bu, çakışma olmaksızın aynı uygulama etki alanında yan yana yüklemek için bir derlemenin farklı sürümlerine ihtiyacınız olduğu anlamına gelir. Örneğin, aynı basit ada sahip derlemelerde bir API'nin farklı uzantıları varsa, güçlü adlandırma derlemenin her sürümü için benzersiz bir kimlik sağlar.

- Derlemenizi kullanarak uygulamaların performansını olumsuz etkilemek istemezsiniz, bu nedenle derlemenin etki alanı nötr olmasını istersiniz. Etki alanı nötr bir derleme genel derleme önbelleğine yüklü olması gerektiğinden, bu güçlü adlandırma gerektirir.

- Yayımcı ilkesini uygulayarak uygulamanız için servis işlemlerini merkezileştirmek istiyorsunuz, bu da derlemenin genel derleme önbelleğine yüklenmesi gerektiği anlamına gelir.

Açık kaynak kodlu bir geliştiriciyseniz ve güçlü bir derlemenin kimlik avantajlarını istiyorsanız, kaynak denetim sisteminizde bir derlemeyle ilişkili özel anahtarı denetlemeyi düşünün.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel montaj önbelleği](../../framework/app-domains/gac.md)
- [Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama](sign-strong-name.md)
- [Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
