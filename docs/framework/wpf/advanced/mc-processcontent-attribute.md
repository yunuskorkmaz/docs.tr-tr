---
title: mc:ProcessContent Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: e625d99cdb30368a798b4829d103f8f26b2c9274
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991860"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent Özniteliği
En üst [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğe, [mc: Ignorable özniteliği](mc-ignorable-attribute.md)belirtildiğinde bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tarafından yoksayılabilir olsa bile, hangi öğelerin ilgili üst öğeler tarafından işlenmesi gereken içeriğe sahip olması gerektiğini belirtir. Öznitelik `mc:ProcessContent` , hem özel ad alanı eşlemesi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de sürüm oluşturma için biçimlendirme uyumluluğunu destekler.  
  
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
|*Thiselementcanbeyoksayıldı*|Temel alınan tür çözümlenemiyorsa, işlemci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamaları tarafından yoksayılabilir bir öğe.|  
|*içeriði*|*Thiselementcanbeyoksayıldı* , yoksayılabilir olarak işaretlenmiş. İşlemci bu öğeyi yok saysa, *[Content]* *nesne*tarafından işlenir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan bir öğe içindeki içeriği yoksayar. Tarafından `mc:ProcessContent`belirli bir öğe belirtebilirsiniz ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci, yoksayılan öğe içindeki içeriği işlemeye devam eder. Bu, genellikle içerik birkaç etiket içinde iç içe ise, en az biri yoksayılabilir ve en az bir tane yok sayılabilir olmayan bir şekilde kullanılır.  
  
 Öznitelikte bir boşluk ayırıcısı kullanılarak birden çok önek belirtilebilir, örneğin: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 Ad `http://schemas.openxmlformats.org/markup-compatibility/2006` alanı, SDK 'nın bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar. Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](https://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [mc:Ignorable Özniteliği](mc-ignorable-attribute.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
