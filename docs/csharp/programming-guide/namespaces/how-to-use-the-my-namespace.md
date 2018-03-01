---
title: "Nasıl yapılır: Ad Alanım'ı Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3564c594a5fbb9bd05a956e5c12bbb173d2db51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Nasıl yapılır: Ad Alanım'ı Kullanma (C# Programlama Kılavuzu)
<xref:Microsoft.VisualBasic.MyServices> Ad alanı (`My` Visual Basic'te) .NET Framework sınıfları, bilgisayar, uygulama, ayarları, kaynaklar vb. ile etkileşime giren kod yazmayı sağlayan bir dizi kolay ve sezgisel erişim sağlar. İlk olarak Visual Basic ile kullanılmak üzere tasarlanmış olsa da `MyServices` ad alanı, C# uygulamalarda kullanılabilir.  
  
 Kullanma hakkında daha fazla bilgi için `MyServices` ad alanı Visual Basic'teki bkz [ile geliştirme My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Başvuru ekleme  
 Kullanmadan önce `MyServices` sınıfları çözümünüzde, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Visual Basic kitaplığına bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ tıklatın **başvuruları** düğümü ve select **Başvuru Ekle**.  
  
2.  Zaman **başvuruları** iletişim kutusu görüntülenirse, listede aşağı kaydırın ve Microsoft.VisualBasic.dll içinde seçin.  
  
     Aşağıdaki satırda eklemek isteyebilirsiniz `using` programınızı başlangıcında bölümü.  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte yer alan çeşitli statik yöntemlerini çağıran `MyServices` ad alanı. Bu kodu derlemek bir başvuru Microsoft.VisualBasic.dll içinde projeye eklenmelidir.  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Tüm sınıflarda `MyServices` ad alanı bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değil. Bu örnekte, statik yöntemler, parçası olan <xref:Microsoft.VisualBasic.FileIO.FileSystem>, hangi de VisualBasic.dll içinde bulunan kullanılabilir. Örneğin, şöyle bir dizini çoğaltmak için bu tür bir yöntem kullanın:  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ad alanları](../../../csharp/programming-guide/namespaces/index.md)  
 [Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)
