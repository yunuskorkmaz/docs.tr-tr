---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 157060e784e4169ac8e31c6028ed65f0a9568e0f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373588"
---
# <a name="how-to-create-a-simple-binding"></a>Nasıl yapılır: Basit bir Bağlama Oluşturma
Bu örnekte basit bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`. `Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.  
  
 İçeren vurgulanan satırın `<src>` öğesi aşağıdaki örnekte başlatır `Person` nesnesi ile bir `PersonName` özelliği değerinin `Joe`. Bu yapılır `Resources` bölümünde ve atanmış bir `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 İçeren vurgulanan satırın `<TextBlock>` öğesi ardından bağlar <xref:System.Windows.Controls.TextBlock> denetimini `PersonName` özelliği. Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "Joe" değeriyle görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
