---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555025"
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
