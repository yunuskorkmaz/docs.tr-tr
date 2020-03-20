---
title: Sürüm 2.0'da System.Uri ad alanında yapılan değişiklikler
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642769"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Sürüm 2.0'da System.Uri ad alanında yapılan değişiklikler

<xref:System.Uri?displayProperty=nameWithType> Sınıfta çeşitli değişiklikler yapıldı. Bu değişiklikler yanlış davranışı, gelişmiş kullanılabilirliği ve gelişmiş güvenliği düzelttirdi.

## <a name="obsolete-and-deprecated-members"></a>Eski ve yıkıntılı Üyeler

 Kurucular:

- `dontEscape` Parametresi olan tüm yapıcılar.

 Yöntemler:

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a>Değişiklikler

- Sorgu bölümü (dosya, ftp ve diğerleri) olmadığı bilinen URI düzenleri için '?' karakteri her zaman kaçar <xref:System.Uri.Query%2A> ve bir bölümün başlangıcı olarak kabul edilmez.

- Örtük dosya URI'leri `c:\directory\file@name.txt`(formdan), parça karakteri ('#') her zaman tam <xref:System.Uri.LocalPath%2A> `true`unescaping istenmedikçe veya .

- UNC hostname desteği kaldırıldı; uluslararası ana bilgisayar adlarını temsil eden IDN belirtimi kabul edilmiştir.

- <xref:System.Uri.LocalPath%2A>her zaman tamamen kaçılmamış bir dize döndürür.

- <xref:System.Uri.ToString%2A>kaçan bir '%', '?'veya '#' karakterinden kaçmaz.

- <xref:System.Uri.Equals%2A>şimdi eşitlik <xref:System.Uri.Query%2A> denetimindeki bölümü içerir.

- "==" ve "!=" işleçleri geçersiz <xref:System.Uri.Equals%2A> kılınmış ve yönteme bağlanır.

- <xref:System.Uri.IsLoopback%2A>şimdi tutarlı sonuçlar üretir.

- URI "`file:///path`" artık `file://path`.

- "#" artık bir ana bilgisayar adı sonlandırıcısı olarak kabul edilmektedir. Yani, `http://contoso.com#fragment` şimdi dönüştürülür `http://contoso.com/#fragment`.

- Bir temel URI'yi bir parçayla birleştirirken bir hata düzeltildi.

- Bir hata <xref:System.Uri.HostNameType%2A> giderilmiştir.

- NNTP ayrıştırma bir hata giderilmiştir.

- Formun bir URI HTTP:contoso.com şimdi bir ayrıştırma özel atar.

- Framework, bir URI'deki userinfo'yu doğru şekilde işler.

- URI yol sıkıştırma, bozuk bir URI'nin dosya sisteminde kökün üzerinde geçememesi için sabitlenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Uri?displayProperty=nameWithType>
