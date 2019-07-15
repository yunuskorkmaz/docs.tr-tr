---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856988"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Unicode UNC paylaşımlarını benzer bir URI'leri izin ver

|   |   |
|---|---|
|Ayrıntılar|İçinde <xref:System.Uri?displayProperty=fullName>, bir dosya oluşturmak URI içeren iki UNC paylaşım adını ve Unicode karakterler artık sonuçlanır geçersiz iç durum ile bir URI. Yalnızca aşağıdakilerin tümü doğru olduğunda davranışı değiştirir:<ul><li>URI şeması bulunuyor <code>file:</code> ve dört veya daha fazla eğik çizgiyle izlenir.</li><li>Ana bilgisayar adı, alt çizgi veya başka ayrılmamış bir simge ile başlar.</li><li>URI, Unicode karakterler içeriyor.</li></ul>|
|Öneri|Tutarlı bir şekilde Unicode karakterler içeren URI'leri ile çalışan uygulamalar, kısıtlanmamışsa UNC paylaşımlarına başvuruları engellemek için bu davranışı kullanabilirdiniz. Bu uygulamaların kullanması gereken <xref:System.Uri.IsUnc> yerine.|
|`Scope`|Kenar|
|Version|4.7.2|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

