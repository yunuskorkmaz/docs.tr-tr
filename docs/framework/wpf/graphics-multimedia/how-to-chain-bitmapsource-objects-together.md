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
ms.openlocfilehash: 403a2a8683e65fd71df89befd59744ac3fe6200c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785664"
---
# <a name="how-to-chain-bitmapsource-objects-together"></a>Nasıl yapılır: BitmapSource Nesnelerini Birbirlerine Bağlayarak Zincir Oluşturma
Bu örnek birden çok görüntü kaynağı için zincirleme tarafından etkileri çeşitli nasıl uygulayabileceğiniz gösterir <xref:System.Windows.Media.Imaging.BitmapSource> birlikte türetilmiş nesneler.  
  
 Aşağıdaki örnek, çevirme ve görüntü kaynağını piksel biçimini değiştirmek için zincirleme kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[ImagingSnippetGallery_snip#ChainedBitmapSourcesXamlExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_snip/CS/ChainedBitmapSourcesExample.xaml#chainedbitmapsourcesxamlexamplewholepage)]  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/ChainedBitmapSourcesExample.cs#chainedbitmapsourcescodeexamplewholepage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/ChainedBitmapSourcesExample.vb#chainedbitmapsourcescodeexamplewholepage)]
