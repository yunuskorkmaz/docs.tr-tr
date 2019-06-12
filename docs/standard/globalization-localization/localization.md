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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79ec24d16b43bd8e1312b3425e618adf163edd24
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834017"
---
# <a name="localization"></a>Yerelleştirme

Yerelleştirme uygulama destekleyen her bir kültür için yerelleştirilmiş sürüm uygulamanın kaynaklarını çevirmeyi işlemidir. Yalnızca tamamladıktan sonra yerelleştirme adıma devam etmelisiniz [Yerelleştirilebilirlik gözden geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md) yazılırlar yerelleştirme için hazır olduğunu doğrulamak için adım.

Yerelleştirme için hazır bir uygulama iki kavramsal bloklarda ayrılır: tüm kullanıcı arabirimi öğeleri ve yürütülebilir kod içeren bir bloğu içeren bir blok. Kullanıcı arabirimi bloğu, dizeler, hata iletileri, iletişim kutuları, menüler, vb. bağımsız kültür için katıştırılmış nesne kaynakları gibi yalnızca yerelleştirilebilir kullanıcı arabirimi öğeleri içeriyor. Kod bloğu tüm desteklenen kültürler tarafından kullanılmak üzere yalnızca uygulama kodunu içerir. Ortak dil çalışma zamanı, bir uygulamanın yürütülebilir kodunun kaynaklarından ayıran bir uydu derleme kaynağı modeli destekler. Bu model uygulama hakkında daha fazla bilgi için bkz. [.NET kaynaklarında](../../../docs/framework/resources/index.md).

Uygulamanızı yerelleştirilmiş her sürümü için yerelleştirilmiş kullanıcı arabirimi blok hedef kültüre uygun dili erişimcisine içeren yeni bir uydu derlemesini ekleyin. Kod bloğu tüm kültürler için aynı kalmalıdır. Kullanıcı arabirimi blok kod bloğu ile yerelleştirilmiş bir sürümünü birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.

Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe), hızlı bir şekilde hedef kültür için Windows formlarını yerelleştirmeye olanak tanır Windows Yazılım Geliştirme Seti (SDK) sağlar. Bu aracı kullanma hakkında daha fazla bilgi için bkz: [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Yerelleştirilebilirlik Gözden Geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md)
- [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
