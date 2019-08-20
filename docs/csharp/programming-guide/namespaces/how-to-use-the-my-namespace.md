---
title: 'Nasıl yapılır: My Namespace- C# Programming kılavuzunu kullanın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: ff00a60d92ec6abbeb257abec76ed2812867f651
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588870"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Nasıl yapılır: My Namespace (C# Programlama Kılavuzu) kullanın
Ad alanı (`My` Visual Basic), bir dizi .NET Framework sınıfa kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşimde bulunan bir kod yazmanıza olanak tanır. <xref:Microsoft.VisualBasic.MyServices> Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarda kullanılabilir.  
  
 Visual Basic `MyServices` ad alanını kullanma hakkında daha fazla bilgi için, bkz. [ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Başvuru ekleme  
 Çözümünüzde `MyServices` sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Visual Basic kitaplığına bir başvuru eklemek için  
  
1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.  
  
2. **Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft. VisualBasic. dll ' i seçin.  
  
     Programınızın başlangıcında `using` bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `MyServices` ad alanında bulunan çeşitli statik yöntemleri çağırır. Bu kodun derlenmesi için projeye Microsoft. VisualBasic. DLL başvurusunun eklenmesi gerekir.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 `MyServices` Ad alanındaki sınıfların tümü bir C# uygulamadan çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir. Bu durumda, ' ın bir <xref:Microsoft.VisualBasic.FileIO.FileSystem>parçası olan statik yöntemler bunun yerine VisualBasic. dll içinde de kullanılabilir. Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanları](./index.md)
- [Ad Alanlarını Kullanma](./using-namespaces.md)
