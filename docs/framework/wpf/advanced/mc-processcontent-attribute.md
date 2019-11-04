---
title: mc:ProcessContent Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: dde304cc2b9db9cb01f9264ca1359b8979512cfa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458785"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent Özniteliği
En üst öğe, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından, [mc: Ignorable özniteliği](mc-ignorable-attribute.md)belirtilirken yok sayılsa bile, hangi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğelerinin hala ilgili üst öğeler tarafından işlenmesi gerektiğini belirtir. `mc:ProcessContent` özniteliği, hem özel ad alanı eşlemesi hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürümü oluşturma için biçimlendirme uyumluluğunu destekler.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
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
|*ıgnorableprefix*|XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi.|  
|*ıgnorableuri*|XML 1,0 belirtimine göre bir ad alanı atamak için geçerli bir URI.|  
|*Thiselementcanbeyoksayıldı*|Temel alınan tür çözümlenemiyorsa, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] işlemci uygulamaları tarafından yoksayılabilir bir öğe.|  
|*içeriði*|*Thiselementcanbeyoksayıldı* , yoksayılabilir olarak işaretlenmiş. İşlemci bu öğeyi yok saysa, *[Content]* *nesne*tarafından işlenir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi yoksayılan bir öğe içindeki içeriği yoksayar. `mc:ProcessContent`tarafından belirli bir öğe belirtebilirsiniz ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi yoksayılan öğe içindeki içeriği işlemeye devam eder. Bu, genellikle içerik birkaç etiket içinde iç içe ise, en az biri yoksayılabilir ve en az bir tane yok sayılabilir olmayan bir şekilde kullanılır.  
  
 Öznitelikte bir boşluk ayırıcısı kullanılarak birden çok önek belirtilebilir, örneğin: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 `http://schemas.openxmlformats.org/markup-compatibility/2006` ad alanı, SDK 'nın bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar. Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](https://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [mc:Ignorable Özniteliği](mc-ignorable-attribute.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
