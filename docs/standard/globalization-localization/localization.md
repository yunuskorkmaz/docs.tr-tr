---
title: "Yerelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 952696cf813a4bd0915f85a02946489d389d23e7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="localization"></a>Yerelleştirme
Yerelleştirme uygulama destekleyecek her kültür için yerelleştirilmiş sürümleri içine uygulamanın kaynaklarını çevirme işlemidir. Yalnızca tamamladıktan sonra yerelleştirme adıma devam etmemelisiniz [Yerelleştirilebilirlik gözden geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md) globalized uygulama yerelleştirme için hazır olduğunu doğrulamak için adım.  
  
 Yerelleştirme için hazır bir uygulama, iki kavramsal blokları, tüm kullanıcı arabirimi öğeleri içeren bir blok ve yürütülebilir kodu içeren bir blok ayrılır. Kullanıcı arabirimi bloğu yalnızca dizeleri, hata iletileri, iletişim kutuları, menüler, vb. bağımsız kültür için katıştırılmış nesne kaynakları gibi yerelleştirilebilir kullanıcı arabirimi öğeleri içerir. Kod bloğu tarafından desteklenen tüm kültürler kullanılacak yalnızca uygulama kodunu içerir. Ortak dil çalışma zamanı uygulamanın yürütülebilir kod kaynaklarıyla ayıran bir uydu derleme kaynağı modelini destekler. Bu model uygulama hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../docs/framework/resources/index.md).  
  
 Uygulamanızın yerelleştirilmiş her sürümü için hedef kültürle için uygun dili erişimcisine yerelleştirilmiş kullanıcı arabirimi blok içeren yeni bir uydu derleme ekleyin. Tüm kültürler için kod bloğu aynı kalması gerekir. Kod bloğu ile kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümün birleşimi, uygulamanızın yerelleştirilmiş bir sürümün üretir.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe), hızlı bir şekilde Windows Forms için hedef kültürlere yerelleştirme sayesinde sağlar. Bu aracı kullanmayla ilgili daha fazla bilgi için bkz: [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)  
 [Yerelleştirilebilirlik Gözden Geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md)  
 [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
