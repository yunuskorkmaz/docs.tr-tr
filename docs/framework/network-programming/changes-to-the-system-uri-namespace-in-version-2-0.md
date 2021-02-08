---
description: "Hakkında daha fazla bilgi edinin: sürüm 2,0 ' de System. Uri ad alanındaki değişiklikler"
title: Sürüm 2,0 ' de System. Uri ad alanındaki değişiklikler
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 8b5e2f2b3b59fba96e20e40a4df18273a2f6034f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791627"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Sürüm 2,0 ' de System. Uri ad alanındaki değişiklikler

Sınıfta birkaç değişiklik yapılmıştır <xref:System.Uri?displayProperty=nameWithType> . Bu değişiklikler hatalı davranışı, gelişmiş kullanılabilirliği ve geliştirilmiş güvenliği düzelttik.

## <a name="obsolete-and-deprecated-members"></a>Kullanımdan kaldırılan ve kullanım dışı bırakılmış Üyeler

 Kurucu

- Parametresi olan tüm oluşturucular `dontEscape` .

 Yöntem

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a>Değişiklikler

- Bir sorgu bölümüne (dosya, FTP ve diğerleri) sahip olmadığı bilinen URI şemaları için, '? ' karakteri her zaman kaçışın ve bir parçanın başlangıcını kabul etmez <xref:System.Uri.Query%2A> .

- Örtük dosya URI 'Leri (form) için `c:\directory\file@name.txt` , tam kaçış istenmediği veya olduğu müddetçe, parça karakteri (' # ') her zaman atlanmalıdır <xref:System.Uri.LocalPath%2A> `true` .

- UNC konak adı desteği kaldırıldı; Uluslararası ana bilgisayar adlarını temsil eden ıDN belirtimi benimsendi.

- <xref:System.Uri.LocalPath%2A> her zaman tamamen kaçışsız bir dize döndürür.

- <xref:System.Uri.ToString%2A> kaçışın '% ', '? ' veya ' # ' karakterinin kaçış yapmaz.

- <xref:System.Uri.Equals%2A> Artık <xref:System.Uri.Query%2A> eşitlik denetiminin bölümünü içerir.

- "= =" Ve "! =" işleçleri geçersiz kılınır ve <xref:System.Uri.Equals%2A> yöntemine bağlanır.

- <xref:System.Uri.IsLoopback%2A> Artık tutarlı sonuçlar üretir.

- "" URI 'SI `file:///path` artık öğesine çevrilmedi `file://path` .

- "#" artık ana bilgisayar adı Sonlandırıcı olarak tanınıyor. Diğer bir deyişle, `http://contoso.com#fragment` Şimdi öğesine dönüştürülür `http://contoso.com/#fragment` .

- Temel URI 'yi bir parçaya birleştirilirken bir hata düzeltildi.

- İçindeki bir hata <xref:System.Uri.HostNameType%2A> düzeltildi.

- NNTP ayrıştırmasındaki bir hata düzeltildi.

- HTTP:contoso. com biçiminde bir URI artık ayrıştırma özel durumu oluşturuyor.

- Framework bir URI 'de UserInfo doğru şekilde işler.

- URI yolu sıkıştırması, bozuk bir URI 'nin kök üzerindeki dosya sisteminde geçiş yapmasını sağlamak için düzeltilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Uri?displayProperty=nameWithType>
