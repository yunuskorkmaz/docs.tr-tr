---
title: Yerelleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 89851c42570f301bee8a3eca744eb5d069347d4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120868"
---
# <a name="localization"></a>Yerelleştirme

Yerelleştirme, uygulamanın kaynaklarını, uygulamanın destekleyeceği her kültür için yerelleştirilmiş sürümlere çevirme işlemidir. Globalized uygulamanın yerelleştirme için hazır olduğunu doğrulamak için yerelleştirme adımına yalnızca [Yerelleştirilebilirlik Gözden Geçirme](../../../docs/standard/globalization-localization/localizability-review.md) adımını tamamladıktan sonra devam etmelisiniz.

Yerelleştirme için hazır bir uygulama iki kavramsal bloka ayrılır: tüm kullanıcı arabirimi öğelerini içeren bir blok ve yürütülebilir kod içeren bir blok. Kullanıcı arabirimi bloğu, yalnızca dizeleri, hata iletileri, iletişim kutuları, menüler, katıştırılmış nesne kaynakları ve benzeri nötr kültür için gibi yerelleştirilebilir kullanıcı arabirimi öğeleri içerir. Kod bloğu yalnızca desteklenen tüm kültürler tarafından kullanılacak uygulama kodunu içerir. Ortak dil çalışma süresi, bir uygulamanın yürütülebilir kodunu kaynaklarından ayıran bir uydu derleme kaynak modelini destekler. Bu modeli uygulama hakkında daha fazla bilgi için [.NET'teki Kaynaklar'a](../../../docs/framework/resources/index.md)bakın.

Uygulamanızın her yerelleştirilmiş sürümü için, hedef kültür için uygun dile çevrilmiş yerelleştirilmiş kullanıcı arabirimi bloğunu içeren yeni bir uydu derlemesi ekleyin. Tüm kültürler için kod bloğu aynı kalmalıdır. Kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümünün kod bloğuyla birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.

Windows Yazılım Geliştirme Kiti (SDK), hedef kültürler için Windows Formlarını hızla yerelleştirmenize olanak tanıyan Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe) sağlar. Bu aracı kullanma hakkında daha fazla bilgi için [Winres.exe (Windows Forms Resource Editor) (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Yerelleştirilebilirlik İnceleme](../../../docs/standard/globalization-localization/localizability-review.md)
- [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)
- [Masaüstü Uygulamalarında Kaynaklar](../../../docs/framework/resources/index.md)
