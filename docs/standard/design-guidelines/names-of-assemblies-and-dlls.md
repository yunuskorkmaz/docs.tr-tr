---
title: Derlemeler ve DLL adları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6cf175472d68e99598dd56e170bee3d37ae3c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570438"
---
# <a name="names-of-assemblies-and-dlls"></a>Derlemeler ve DLL adları
Derleme dağıtımı ve yönetilen kod programlar kimliğini birimidir. Genellikle bir veya daha çok dosya derlemeleri yayılabilir karşın, bir derlemeyi bire bir DLL ile eşler. Bu nedenle, bu bölümde daha sonra derleme adlandırma kurallarına eşlenen yalnızca DLL adlandırma kuralları, açıklanmaktadır.  
  
 **✓ YAPMAK** derlemenizi System.Data gibi işlevleri büyük boyutta önermek DLL'ler için adları'ı seçin.  
  
 Derleme ve DLL adları ad alanı adları için karşılık gelen gerekmez, ancak ad derlemeleri adlandırırken izlemek makul. Bir iyi derlemesinde bulunan ad alanları ortak önekini temel DLL adlandırmak için udur. Örneğin, iki ad alanı, bir derleme `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature`, çağrılabilir `MyCompany.MyTechnology.dll`.  
  
 **✓ DÜŞÜNÜN** göre aşağıdaki düzeni DLL'leri adlandırma:  
  
 `<Company>.<Component>.dll`  
  
 Burada `<Component>` bir veya daha fazla nokta ayrılmış yan tümceleri içerir. Örneğin:  
  
 `Litware.Controls.dll`.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
