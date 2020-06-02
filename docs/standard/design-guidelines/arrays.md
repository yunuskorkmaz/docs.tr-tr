---
title: Diziler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 30277507050091de6b1e9293401d61ac5e351a1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280627"
---
# <a name="arrays"></a>Diziler
✔️ ortak API 'lerde diziler üzerinde koleksiyonları kullanmayı tercih eder. [Koleksiyonlar](guidelines-for-collections.md) bölümü koleksiyonlar ve diziler arasında nasıl seçim yapılacağı hakkında ayrıntılar sağlar.

 ❌Salt okunurdur dizi alanlarını kullanmayın. Alanın kendisi salt okunurdur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.

 ✔️ çok boyutlu diziler yerine pürüzlü Diziler kullanmayı düşünün.

 Sivri dizi öğeleri de diziler olan bir dizidir. Öğeleri oluşturan diziler farklı boyutlarda olabilir ve çok boyutlu dizilere kıyasla bazı veri kümeleri (örn. seyrek matris) için daha az harcanan alana sahiptir. Ayrıca, CLR, basit diziler üzerinde dizin işlemlerini iyileştirir, bu nedenle bazı senaryolarda çalışma zamanı daha iyi bir performans sergilebilirler.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)
