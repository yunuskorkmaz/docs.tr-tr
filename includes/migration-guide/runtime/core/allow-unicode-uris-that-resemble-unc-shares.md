---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236160"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Unicode UNC paylaşımlarını benzer bir URI'leri izin ver

|   |   |
|---|---|
|Ayrıntılar|İçinde <xref:System.Uri?displayProperty=fullName>, bir dosya oluşturmak URI içeren iki UNC paylaşım adını ve Unicode karakterler artık sonuçlanır geçersiz iç durum ile bir URI. Yalnızca aşağıdakilerin tümü doğru olduğunda davranışı değiştirir:<ul><li>URI şeması bulunuyor <code>file:</code> ve dört veya daha fazla eğik çizgiyle izlenir.</li><li>Ana bilgisayar adı, alt çizgi veya başka ayrılmamış bir simge ile başlar.</li><li>URI, Unicode karakterler içeriyor.</li></ul>|
|Öneri|Tutarlı bir şekilde Unicode karakterler içeren URI'leri ile çalışan uygulamalar, kısıtlanmamışsa UNC paylaşımlarına başvuruları engellemek için bu davranışı kullanabilirdiniz. Bu uygulamaların kullanması gereken <xref:System.Uri.IsUnc> yerine.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
