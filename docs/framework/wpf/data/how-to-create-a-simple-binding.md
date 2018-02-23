---
title: "Nasıl yapılır: Basit bir Bağlama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a>Nasıl yapılır: Basit bir Bağlama Oluşturma
Bu örnek nasıl basit bir oluşturulacağını gösterir <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sahip olduğunuz bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`. `Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.  
  
 İçeren vurgulanan satırı `<src>` öğesi aşağıdaki örnekte başlatır `Person` nesnesi ile bir `PersonName` özellik değerinin `Joe`. Bu yapılır `Resources` bölümünde ve atanmış bir `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 İçeren vurgulanan satırı `<TextBlock>` öğesi sonra bağlar <xref:System.Windows.Controls.TextBlock> denetimini `PersonName` özelliği. Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "Can" değeriyle belirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
