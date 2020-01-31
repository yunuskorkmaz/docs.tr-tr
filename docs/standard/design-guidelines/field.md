---
title: Alan Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: c00929ca499e39bd4e24d482c9413beb9cccddc1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741603"
---
# <a name="field-design"></a>Alan Tasarımı
Kapsülleme prensibi, nesne odaklı tasarımda en önemli olmaların biridir. Bu ilke, bir nesne içinde depolanan verilerin yalnızca o nesnenin erişimine açık olması gerektiğini belirtir.

 Prensibi yorumlamak için kullanışlı bir yol, türün (ad veya tür değişiklikleri) alanlara yapılan değişikliklerin, türün üyeleri için dışında bir kod olmadan yapılabilmesi için bir türün tasarlanmalıdır. Bu yorum hemen tüm alanların özel olması gerektiğini gösterir.

 Bu katı kısıtlamadan yalnızca sabit ve statik salt okunurdur alanları hariç tutduk, çünkü bu tür alanlar, neredeyse tanım için hiçbir şekilde değişiklik gerektirmez.

 ❌ ortak veya korumalı örnek alanlar sağlamaz.

 Genel veya korumalı hale getirmek yerine alanlara erişim için özellikler sağlamalısınız.

 ✔️ hiçbir şekilde değişmeyecek sabitler için sabit alanlar kullanın.

 Derleyici const alanlarının değerlerini doğrudan çağıran koda dönüştürür. Bu nedenle, sabit değerler hiçbir şekilde uyumluluk riski olmadan değiştirilemez.

 ✔️ önceden tanımlanmış nesne örnekleri için ortak statik `readonly` alanlarını kullanın.

 Türün önceden tanımlanmış örnekleri varsa, bunları türün kendisine ait public salt okunurdur statik alanlar olarak bildirin.

 ❌, `readonly` alanlara kesilebilir türlerin örneklerini atamayın.

 Kesilebilir tür, örneklendirildikten sonra değiştirilebilen örneklere sahip bir türdür. Örneğin, diziler, en çok koleksiyonlar ve akışlar değişebilir türlerdir, ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>ve <xref:System.String?displayProperty=nameWithType> sabittir. Bir başvuru türü alanındaki salt okunurdur değiştirici, alanda depolanan örneğin değiştirilmesini önler, ancak örneği değiştiren Üyeler çağırarak alanın örnek verilerinin değiştirilmesini engellemez.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
