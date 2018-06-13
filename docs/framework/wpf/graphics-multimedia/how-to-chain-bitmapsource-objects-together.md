---
title: 'Nasıl yapılır: BitmapSource Nesnelerini Birbirlerine Bağlayarak Zincir Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BitmapSource objects [WPF], chaining
- graphics [WPF], chaining BitmapSource objects
- chaining BitmapSource objects [WPF]
ms.assetid: 32d88853-395b-4855-9685-51a482a3b421
ms.openlocfilehash: 5c70b6ec132234959404203fb62567ddb0acf762
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558871"
---
# <a name="how-to-chain-bitmapsource-objects-together"></a>Nasıl yapılır: BitmapSource Nesnelerini Birbirlerine Bağlayarak Zincir Oluşturma
Bu örnek bir görüntü kaynağı zincirleme tarafından çeşitli efektleri nasıl uygulayabileceğiniz birden çok gösterir <xref:System.Windows.Media.Imaging.BitmapSource> nesnelerin araya türetilmiş.  
  
 Aşağıdaki örnek, ters çevirmek ve kaynak görüntüsünün piksel biçimini değiştirmek için zincirleme kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[ImagingSnippetGallery_snip#ChainedBitmapSourcesXamlExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_snip/CS/ChainedBitmapSourcesExample.xaml#chainedbitmapsourcesxamlexamplewholepage)]  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/ChainedBitmapSourcesExample.cs#chainedbitmapsourcescodeexamplewholepage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/ChainedBitmapSourcesExample.vb#chainedbitmapsourcescodeexamplewholepage)]
