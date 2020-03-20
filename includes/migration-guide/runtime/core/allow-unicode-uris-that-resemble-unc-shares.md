---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856988"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>UNC hisselerine benzeyen URI'lerde Unicode'a izin ver

|   |   |
|---|---|
|Ayrıntılar|Hem <xref:System.Uri?displayProperty=fullName>UNC hisse adı hem de Unicode karakterleri içeren bir dosya URI'nin oluşturulması artık geçersiz iç durumu olan bir URI ile sonuçlanmaz. Davranış yalnızca aşağıdakilerin tümü doğru olduğunda değişecektir:<ul><li>URI düzeni <code>file:</code> vardır ve dört veya daha fazla kesikler tarafından takip edilir.</li><li>Ana bilgisayar adı bir alt puan veya diğer rezerve edilmeyen bir sembolle başlar.</li><li>URI, Unicode karakterleri içerir.</li></ul>|
|Öneri|Sürekli Unicode içeren URI'lerle çalışan uygulamalar, unc hisselerine yapılan atıflara izin vermemek için bu davranışı kullanmış olabilir. Bu uygulamaları yerine <xref:System.Uri.IsUnc> kullanmalısınız.|
|Kapsam|Edge|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
