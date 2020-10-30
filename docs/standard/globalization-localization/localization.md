---
title: Localization (Yerelleştirme)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET], localization
- globalization [.NET], localization
- code blocks
- international applications [.NET], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: e92184f48b2d2255138da5b2a6e7e2977a95e2e3
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93062964"
---
# <a name="localization"></a>Localization (Yerelleştirme)

Yerelleştirme, uygulamanın destekleyeceği her kültür için bir uygulamanın kaynaklarını yerelleştirilmiş sürümlere çevirme işlemidir. Genelleştirilmiş uygulamasının yerelleştirme için hazırlanmaya devam ettiğini doğrulamak için yerelleştirme adımına yalnızca [Yerelleştirilebilirlik gözden geçirmesi](localizability-review.md) adımını tamamladıktan sonra ilerlemeniz gerekir.

Yerelleştirme için hazırlanma bir uygulama iki kavramsal blok halinde ayrılmıştır: tüm Kullanıcı arabirimi öğelerini ve yürütülebilir kodu içeren bir bloğu içeren bir blok. Kullanıcı arabirimi bloğu, bağımsız kültür için yalnızca dizeler, hata iletileri, iletişim kutuları, menüler, katıştırılmış nesne kaynakları gibi yerelleştirilebilir kullanıcı arabirimi öğelerini içerir. Kod bloğu yalnızca desteklenen tüm kültürler tarafından kullanılacak uygulama kodunu içerir. Ortak dil çalışma zamanı, bir uygulamanın yürütülebilir kodunu kaynaklarından ayıran bir uydu derleme kaynak modeli destekler. Bu modeli uygulama hakkında daha fazla bilgi için bkz. [.net 'Teki kaynaklar](../../framework/resources/index.md).

Uygulamanızın yerelleştirilmiş her sürümü için, hedef kültür için uygun dile çevrilmiş yerelleştirilmiş kullanıcı arabirimi bloğunu içeren yeni bir uydu derlemesi ekleyin. Tüm kültürlerin kod bloğu aynı kalmalıdır. Kod bloğu ile Kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümünün birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.

Windows yazılım geliştirme seti (SDK), hedef kültürler için Windows Forms hızlı bir şekilde yerelleştirebilmenizi sağlayan Windows Forms Kaynak Düzenleyicisi (Winres.exe) sağlar. Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Winres.exe (Windows Forms Kaynak Düzenleyicisi)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve yerelleştirme](index.md)
- [Yerelleştirilebilirlik Incelemesi](localizability-review.md)
- [Genelleştirme](globalization.md)
- [Masaüstü uygulamalarındaki kaynaklar](../../framework/resources/index.md)
