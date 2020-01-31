---
title: Bütünleştirilmiş Kod ve DLL Adları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: f3c5997f777c937e9726b271afa0ae6d7a19b37d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744165"
---
# <a name="names-of-assemblies-and-dlls"></a>Bütünleştirilmiş Kod ve DLL Adları
Derleme, yönetilen kod programlarının dağıtım ve kimlik birimidir. Derlemeler bir veya daha fazla dosyaya yayılabilse de, genellikle bir derleme DLL ile bire bir eşler. Bu nedenle, bu bölümde yalnızca DLL adlandırma kuralları açıklanmakta ve bu daha sonra derleme adlandırma kurallarına eşlenebilir.

 ✔️, System. Data gibi büyük işlevsellik öbeklerini öneren derleme dll 'lerinizin adlarını seçin.

 Derleme ve DLL adlarının ad alanı adlarına karşılık gelmesi gerekmez, ancak derlemeleri adlandırırken ad alanı adını izlemek mantıklı değildir. Parmak izi iyi bir kuralı, derlemede bulunan ad alanlarının ortak ön ekine göre DLL 'yi adlandırma. Örneğin, `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature`iki ad alanı olan bir derleme `MyCompany.MyTechnology.dll`çağrılabilir.

 ✔️ Dll 'Leri aşağıdaki modele göre adlandırmayı düşünün:

 `<Company>.<Component>.dll`

 Burada `<Component>` bir veya daha fazla noktayla ayrılmış yan tümce içerir. Örneğin:

 `Litware.Controls.dll`.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
