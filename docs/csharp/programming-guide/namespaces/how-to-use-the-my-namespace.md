---
title: Benim ad alanım nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700425"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Ad alanım (C# Programlama Kılavuzu) nasıl kullanılır?
<xref:Microsoft.VisualBasic.MyServices> Ad alanı`My` (Visual Basic'te), bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşimedebilen kod lar yazmanızı sağlayan bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar. Başlangıçta Visual Basic ile kullanılmak üzere `MyServices` tasarlanmış olsa da, ad alanı C# uygulamalarında kullanılabilir.  
  
 Visual Basic'teki `MyServices` ad alanını kullanma hakkında daha fazla bilgi [için, Bkz.](../../../visual-basic/developing-apps/development-with-my/index.md)  
  
## <a name="adding-a-reference"></a>Referans Ekleme  
 Çözümdeki `MyServices` sınıfları kullanabilmek için Önce Visual Basic kitaplığına bir başvuru eklemeniz gerekir.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Visual Basic kitaplığına başvuru eklemek için  
  
1. **Çözüm Gezgini'nde,** **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle'yi**seçin.  
  
2. **Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft.VisualBasic.dll'yi seçin.  
  
     Ayrıca, programın başındaki `using` bölüme aşağıdaki satırı eklemek isteyebilirsiniz.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `MyServices` ad alanında bulunan çeşitli statik yöntemleri çağırır. Bu kodun derlemesi için projeye Microsoft.VisualBasic.DLL'ye bir başvuru eklenmesi gerekir.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 `MyServices` Ad alanındaki tüm sınıflar C# uygulamasından çağrılabilir: örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıf uyumlu değildir. Bu özel durumda, visualBasic.dll'de de bulunan statik yöntemler <xref:Microsoft.VisualBasic.FileIO.FileSystem>kullanılabilir. Örneğin, bir dizini çoğaltmak için böyle bir yöntemin nasıl kullanılacağı aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanları](./index.md)
- [Ad Alanlarını Kullanma](./using-namespaces.md)
