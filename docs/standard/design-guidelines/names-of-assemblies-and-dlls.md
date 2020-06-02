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
ms.openlocfilehash: 138ae8154b0d10fb813f0c98ceb7c58a2471b780
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291961"
---
# <a name="names-of-assemblies-and-dlls"></a>Bütünleştirilmiş Kod ve DLL Adları
Derleme, yönetilen kod programlarının dağıtım ve kimlik birimidir. Derlemeler bir veya daha fazla dosyaya yayılabilse de, genellikle bir derleme DLL ile bire bir eşler. Bu nedenle, bu bölümde yalnızca DLL adlandırma kuralları açıklanmakta ve bu daha sonra derleme adlandırma kurallarına eşlenebilir.

 ✔️, System. Data gibi büyük işlevsellik öbeklerini öneren derleme dll 'lerinizin adlarını seçin.

 Derleme ve DLL adlarının ad alanı adlarına karşılık gelmesi gerekmez, ancak derlemeleri adlandırırken ad alanı adını izlemek mantıklı değildir. Parmak izi iyi bir kuralı, derlemede bulunan ad alanlarının ortak ön ekine göre DLL 'yi adlandırma. Örneğin, iki ad alanı olan bir derleme `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature` , çağrılabilir `MyCompany.MyTechnology.dll` .

 ✔️ Dll 'Leri aşağıdaki modele göre adlandırmayı düşünün:

 `<Company>.<Component>.dll`

 Burada `<Component>` bir veya daha fazla noktayla ayrılmış yan tümce bulunur. Örneğin:

 `Litware.Controls.dll`.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
