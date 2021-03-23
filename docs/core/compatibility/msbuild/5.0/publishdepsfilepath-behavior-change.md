---
title: 'Son değişiklik: PublishDepsFilePath davranış değişikliği'
description: .NET 5 ' te, tek dosya uygulamalarında PublishDepsFilePath MSBuild özelliğinin boş olduğu son değişiklik hakkında bilgi edinin.
ms.date: 09/17/2020
ms.openlocfilehash: 845073e73ec6bdf820f28ace487d9ae4d04d0790
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872931"
---
# <a name="publishdepsfilepath-behavior-change"></a>PublishDepsFilePath davranış değişikliği

`PublishDepsFilePath`MSBuild özelliği, tek dosya uygulamaları için boştur. Ayrıca, tek dosya olmayan uygulamalar için, dosya *deps.js* , derleme içinde daha sonra çıkış dizinine kopyalanamayabilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, `PublishDepsFilePath` MSBuild özelliği, tek dosya olmayan uygulamalar için çıkış dizinindeki dosyanın *deps.js* yolu ve tek dosya uygulamalarına yönelik ara dizindeki bir yoldur.

.NET 5 ' den itibaren, `PublishDepsFilePath` tek dosya uygulamaları için boştur ve yeni bir `IntermediateDepsFilePath` özellik ara dizindeki konumdaki *deps.js* belirtir. Ayrıca, tek dosya olmayan uygulamalar için, dosyadaki *deps.js* , `PublishDepsFilePath` derleme içinde daha sonra olana kadar çıkış dizinine (yani, tarafından belirtilen yol) kopyalanmayabilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik birkaç nedenden dolayı yapıldı:

- .NET 5 ' te [geliştirilmiş tek dosya uygulamalarını](https://github.com/dotnet/designs/blob/main/accepted/2020/single-file/design.md) desteklemek için yayımlama mantığının yeniden düzenlenmesi nedeniyle.

- Tek dosya uygulamalarında, *deps.json* önceden paketlenmiş olduktan sonra dosyayı *deps.js* yeniden yazmayı deneyen hedeflere karşı koruma sağlamaya yardımcı olmak için, uygulamayı sessizce etkilememelidir. Bu nedenle, `PublishDepsFilePath` tek dosya uygulamaları için boştur.

## <a name="recommended-action"></a>Önerilen eylem

Dosyayı *deps.js* yeniden yazan hedefler genellikle özelliğini kullanarak bunu yapmanız gerekir `IntermediateDepsFilePath` .

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
