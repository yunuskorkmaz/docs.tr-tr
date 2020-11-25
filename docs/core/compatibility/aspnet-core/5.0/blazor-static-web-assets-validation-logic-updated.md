---
title: 'Son değişiklik: Blazor: statik Web varlıkları için doğrulama mantığı güncelleştirildi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: statik Web varlıkları için güncelleştirilmiş doğrulama mantığı"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f201818c0130739e8da4f42e7b1f3a1987f70d1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761477"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a>Blazor: statik Web varlıkları için doğrulama mantığı güncelleştirildi

ASP.NET Core 3,1 ve Blazor WebAssembly 3,2 ' de statik Web varlıkları için çakışma doğrulamasında bir sorun oluştu. Sorun:

* Razor sınıf kitaplıkları (RCLs) ve Blazor WebAssembly uygulamalarından gelen konak varlıkları ve varlıklar arasında doğru çakışma algılamayı engelledi.
* , Varsayılan olarak, RCLs içindeki statik web varlıklarının ön ek kapsamında sunulduğundan, genellikle Blazor WebAssembly uygulamalarını etkiler `_content/$(PackageId)` .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="old-behavior"></a>Eski davranış

Geliştirme sırasında, bir RCL 'nin statik web varlıklarının aynı konak yolu ana bilgisayar proje varlıkları ile sessizce geçersiz kılınabilir. */Folder/file.txt* adresinden sunulacak statik bir web varlığı tanımlamış bir RCL düşünün. Ana bilgisayar *Wwwroot/klasör/file.txt*' a bir dosya yerleştirirse, sunucudaki dosya, RCL veya Blazor WebAssembly uygulamasındaki dosyayı sessizce yok kılar.

## <a name="new-behavior"></a>Yeni davranış

ASP.NET Core, bu sorunun ne zaman gerçekleştiğini doğru şekilde algılar. İlgili eylemi gerçekleştirebileceğiniz için, çakışmayı kullanıcıya bildirir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Statik web varlıklarının, projenin *Wwwroot* ana bilgisayarındaki dosyalar tarafından geçersiz kılınabilir olması amaçlanmamıştır. Bu dosyaların geçersiz kılınmasına izin verilmesi, tanılanması zor hatalara neden olabilir. Sonuç, yayımlanan uygulamalarda tanımsız davranış değişiklikleri olabilir.

## <a name="recommended-action"></a>Önerilen eylem

Varsayılan olarak, bir RCL dosyasının konaktaki bir dosyayla çakışmasının nedeni yoktur. RCL dosyaları ön ekine sahiptir `_content/${PackageId}` . Blazor WebAssembly dosyaları, çakışma daha kolay hale getiren ana bilgisayar URL 'SI alanının köküne yerleştirilir. Örneğin, Blazor WebAssembly Apps, konağın *Wwwroot* klasörüne de dahil olabileceği bir *tercih edilen Icon. ico* dosyası içerir.

Çakışmanın kaynağı bir RCL dosyası ise, genellikle kodun varlıkları kitaplıktan projenin *Wwwroot* klasörüne kopyalandığı anlamına gelir. Dosyaları kopyalamak için kod yazma, statik web varlıklarının birincil hedefini erteler. Bu hedef, içerik yeni bir derleme tetiklemeye gerek kalmadan güncelleştirildiğinde tarayıcıda güncelleştirmeleri almak için önemlidir.

Bu davranışı korumayı ve dosyayı konakta korumayı seçebilirsiniz. Bunu yapmak için, dosyayı özel bir MSBuild hedefi olan statik Web varlıkları listesinden kaldırın.

Ana bilgisayar projesinin dosyası yerine RCL 'nin dosyasını veya Blazor WebAssembly uygulamasının dosyasını kullanmak için, dosyayı konak projesinden kaldırın.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
