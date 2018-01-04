---
title: "Derlemeler ve DLL adları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76584e0d22b6e651dfd851675a72d1f0cb70feb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-assemblies-and-dlls"></a>Derlemeler ve DLL adları
Derleme dağıtımı ve yönetilen kod programlar kimliğini birimidir. Genellikle bir veya daha çok dosya derlemeleri yayılabilir karşın, bir derlemeyi bire bir DLL ile eşler. Bu nedenle, bu bölümde daha sonra derleme adlandırma kurallarına eşlenen yalnızca DLL adlandırma kuralları, açıklanmaktadır.  
  
 **✓ YAPMAK** derlemenizi System.Data gibi işlevleri büyük boyutta önermek DLL'ler için adları'ı seçin.  
  
 Derleme ve DLL adları ad alanı adları için karşılık gelen gerekmez, ancak ad derlemeleri adlandırırken izlemek makul. Bir iyi derlemesinde bulunan derlemeler ortak önekini temel DLL adlandırmak için udur. Örneğin, iki ad alanı, bir derleme `MyCompany.MyTechnology.FirstFeature` ve `MyCompany.MyTechnology.SecondFeature`, çağrılabilir `MyCompany.MyTechnology.dll`.  
  
 **✓ DÜŞÜNÜN** göre aşağıdaki düzeni DLL'leri adlandırma:  
  
 `<Company>.<Component>.dll`  
  
 Burada `<Component>` bir veya daha fazla nokta ayrılmış yan tümceleri içerir. Örneğin:  
  
 `Litware.Controls.dll`.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
