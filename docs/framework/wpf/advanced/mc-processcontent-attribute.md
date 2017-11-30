---
title: "mc:ProcessContent Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaf83fe66d5367d5e51428cb8f35aa88c12c9c39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent Özniteliği
Belirten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri hala olmalıdır ilgili üst öğeler tarafından işlenen İçerik en yakın üst öğe tarafından yoksayılabilir olsa bile bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtme nedeniyle İşlemci [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) . `mc:ProcessContent` Özniteliği, hem hem de özel ad alanı eşlemesi için biçimlendirme uyumluluğunu destekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*ignorablePrefix*|XML 1.0 belirtimi başına herhangi geçerli önek dizesi.|  
|*ignorableUri*|XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.|  
|*ThisElementCanBeIgnored*|Tarafından göz ardı edilebilir bir öğe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temel alınan tür çözümlenemiyorsa işlemcisi uygulamaları.|  
|*[content]*|*ThisElementCanBeIgnored* yoksayılabilir olarak işaretlenir. Bu öğe işlemci yoksayar, *[content]* tarafından işlenen *nesne*.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar. Belirli bir öğeyi belirtebilirsiniz `mc:ProcessContent`ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içinde içeriği işlemeye devam eder. İçeriği en az biri yoksayılabilir olan ve en az biri yoksayılabilir değil birkaç etiket içinde iç içe ise, bu genellikle kullanılır.  
  
 Birden çok önekleri alan ayırıcı örneğin kullanarak özniteliği belirtilebilir: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Ad alanını tanımlayan diğer öğeleri ve bu alanda belgelenmemiş öznitelikleri [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Daha fazla bilgi için bkz: [XML Biçimlendirmesi Uyumluluk Belirtimi](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
