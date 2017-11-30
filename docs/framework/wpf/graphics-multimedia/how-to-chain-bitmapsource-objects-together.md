---
title: "Nasıl yapılır: BitmapSource Nesnelerini Birbirlerine Bağlayarak Zincir Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BitmapSource objects [WPF], chaining
- graphics [WPF], chaining BitmapSource objects
- chaining BitmapSource objects [WPF]
ms.assetid: 32d88853-395b-4855-9685-51a482a3b421
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47ed4518ec4e703df3af380916cc3756a460e4d1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-chain-bitmapsource-objects-together"></a><span data-ttu-id="9d25a-102">Nasıl yapılır: BitmapSource Nesnelerini Birbirlerine Bağlayarak Zincir Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d25a-102">How to: Chain BitmapSource Objects Together</span></span>
<span data-ttu-id="9d25a-103">Bu örnek bir görüntü kaynağı zincirleme tarafından çeşitli efektleri nasıl uygulayabileceğiniz birden çok gösterir <xref:System.Windows.Media.Imaging.BitmapSource> nesnelerin araya türetilmiş.</span><span class="sxs-lookup"><span data-stu-id="9d25a-103">This example shows how you can apply a variety of effects to an image source by chaining multiple <xref:System.Windows.Media.Imaging.BitmapSource> derived objects together.</span></span>  
  
 <span data-ttu-id="9d25a-104">Aşağıdaki örnek, ters çevirmek ve kaynak görüntüsünün piksel biçimini değiştirmek için zincirleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d25a-104">The following example uses chaining to flip and change the pixel format of the source of an image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d25a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d25a-105">Example</span></span>  
 [!code-xaml[ImagingSnippetGallery_snip#ChainedBitmapSourcesXamlExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_snip/CS/ChainedBitmapSourcesExample.xaml#chainedbitmapsourcesxamlexamplewholepage)]  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/ChainedBitmapSourcesExample.cs#chainedbitmapsourcescodeexamplewholepage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/ChainedBitmapSourcesExample.vb#chainedbitmapsourcescodeexamplewholepage)]
