---
title: "Nasıl yapılır: Ad Alanım'ı Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: a8ec3a96534693142d37d26ac0c08eec9298b178
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526212"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Nasıl yapılır: Ad Alanım'ı Kullanma (C# Programlama Kılavuzu)
<xref:Microsoft.VisualBasic.MyServices> Ad alanı (`My` Visual Basic'te) .NET Framework sınıfları, bilgisayar, uygulama, ayarları, kaynakları ve benzeri ile etkileşime giren bir kod yazmanızı sağlayan bir dizi kolay ve sezgisel erişim sağlar. İlk olarak, Visual Basic ile kullanılmak üzere tasarlanmış olsa da `MyServices` ad alanı, C# uygulamalarında kullanılabilir.  
  
 Kullanma hakkında daha fazla bilgi için `MyServices` ad alanı Visual Basic'teki bkz [ile geliştirme My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Başvuru ekleme  
 Kullanmadan önce `MyServices` sınıfları çözümünüzde, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Visual Basic kitaplığına bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları** düğüm ve select **Başvuru Ekle**.  
  
2.  Zaman **başvuruları** iletişim kutusu görüntülenirse, listede aşağıda kaydırarak ve Microsoft.VisualBasic.dll'ı seçin.  
  
     Aşağıdaki satırda eklemek isteyebilirsiniz `using` , program başlangıcında bölümü.  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte yer alan çeşitli statik yöntemler çağırır `MyServices` ad alanı. Bu kodu derlemek projeye bir başvuru Microsoft.VisualBasic.DLL eklenmesi gerekir.  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Tüm sınıfları `MyServices` ad alanı, bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değil. Bu durumda, statik yöntemler parçası olan <xref:Microsoft.VisualBasic.FileIO.FileSystem>, hangi ayrıca VisualBasic.dll içinde bulunan kullanılabilir. Örneğin, şöyle bir dizini çoğaltmak için bu tür bir yöntem kullanmak:  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)  
- [Ad Alanlarını Kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)
