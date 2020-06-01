---
title: My Namespace-C# programlama kılavuzunu kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 268543980ba891b0b30f393ee8982f2863ba9a71
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241948"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>My ad alanım 'ı kullanma (C# Programlama Kılavuzu)

<xref:Microsoft.VisualBasic.MyServices>Ad alanı ( `My` Visual Basic), bir dizi .net sınıfına kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmek için kod yazmanıza olanak tanır. Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarında kullanılabilir.  
  
 Visual Basic ad alanını kullanma hakkında daha fazla bilgi için `MyServices` , bkz. [ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="add-a-reference"></a>Başvuru ekleme

 `MyServices`Çözümünüzde sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a>Visual Basic kitaplığına bir başvuru ekleme  
  
1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.  
  
2. **Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft. VisualBasic. dll ' i seçin.  
  
     Programınızın başlangıcında bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz `using` .  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, ad alanında bulunan çeşitli statik yöntemleri çağırır `MyServices` . Bu kodun derlenmesi için projeye Microsoft. VisualBasic. DLL başvurusunun eklenmesi gerekir.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 `MyServices`Ad alanındaki sınıfların hepsi bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir. Bu durumda, ' ın bir parçası olan statik yöntemler <xref:Microsoft.VisualBasic.FileIO.FileSystem> bunun yerine VisualBasic. dll içinde de kullanılabilir. Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad alanları](./index.md)
- [Ad alanlarını kullanma](./using-namespaces.md)
