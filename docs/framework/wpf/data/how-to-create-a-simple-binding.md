---
title: "Nasıl yapılır: Basit bir Bağlama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a61844f917539f5d5e7c99299c8a33f4aa18450f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-simple-binding"></a>Nasıl yapılır: Basit bir Bağlama Oluşturma
Bu örnek nasıl basit bir oluşturulacağını gösterir <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sahip olduğunuz bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`. `Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.  
  
 Aşağıdaki örnek başlatır `Person` nesnesi ile bir `PersonName` özellik değerinin `Joe`. Bu yapılır `Resources` bölümünde ve atanmış bir `x:Key`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xaml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 Bağlamak için `PersonName` özelliği aşağıdakileri yapmanız:  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "Can" değeriyle belirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
