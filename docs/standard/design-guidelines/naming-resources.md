---
title: Adlandırma Kaynakları
description: .NET 'teki kaynaklar için adlandırma kılavuzunu gözden geçirerek adlandırma özelliklerine yönelik yönergelere benzer.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 765337bcf9fad4f9a8c9272a15b5c77d02770471
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768254"
---
# <a name="naming-resources"></a>Adlandırma Kaynakları
Yerelleştirilebilir kaynaklara, özellikler gibi belirli nesneler aracılığıyla başvurulabildiğinden, kaynaklarla ilgili adlandırma yönergeleri Özellik yönergelerine benzer.

 ✔️, kaynak anahtarlarında Pascalbüyük harfleri kullanır.

 ✔️, kısa tanımlayıcılar yerine açıklayıcı bir ad sağlar.

 ❌Ana CLR dillerinin dile özgü anahtar sözcüklerini kullanmayın.

 ✔️, adlandırma kaynaklarında yalnızca alfasayısal karakterler ve alt çizgi kullanır.

 ✔️, özel durum iletisi kaynakları için aşağıdaki adlandırma kuralını kullanır.

 Kaynak tanımlayıcısı, özel durum türü adı artı özel durumun kısa bir tanımlayıcısı olmalıdır:

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
