---
title: My Namespace- C# programlama kılavuzunu kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700425"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>My Namespace (C# Programlama Kılavuzu) kullanma
<xref:Microsoft.VisualBasic.MyServices> ad alanı (Visual Basic`My`), bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmek için kod yazmanıza olanak tanır. Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarda kullanılabilir.  
  
 Visual Basic `MyServices` ad alanını kullanma hakkında daha fazla bilgi için, bkz. [Ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Başvuru ekleme  
 Çözümünüzde `MyServices` sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Visual Basic kitaplığına bir başvuru eklemek için  
  
1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.  
  
2. **Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft. VisualBasic. dll ' i seçin.  
  
     Programınızın başlangıcında `using` bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Örnek  
 Bu örnek `MyServices` ad alanında bulunan çeşitli statik yöntemleri çağırır. Bu kodun derlenmesi için projeye Microsoft. VisualBasic. DLL başvurusunun eklenmesi gerekir.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 `MyServices` ad alanındaki sınıfların tümü bir C# uygulamadan çağrılamaz: örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir. Bu durumda, bunun yerine VisualBasic. dll içinde bulunan <xref:Microsoft.VisualBasic.FileIO.FileSystem>parçası olan statik yöntemler de kullanılabilir. Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanları](./index.md)
- [Ad Alanlarını Kullanma](./using-namespaces.md)
