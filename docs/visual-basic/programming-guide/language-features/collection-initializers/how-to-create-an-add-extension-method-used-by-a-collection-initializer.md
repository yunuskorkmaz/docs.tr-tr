---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: c36fab6635a9f7820c52c5f73c20487b92879b9a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086354"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma (Visual Basic)

Koleksiyon oluşturmak için bir koleksiyon başlatıcısı kullandığınızda, Visual Basic derleyici, `Add` yöntemi için parametrelerin `Add` koleksiyon başlatıcısındaki değerlerin türleriyle eşleştiği koleksiyon türünde bir yöntemi arar. Bu `Add` Yöntem, koleksiyonu koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılır.  
  
 Eşleşen `Add` bir yöntem yoksa ve koleksiyon için kodu değiştiremeyeceğiniz takdirde, `Add` koleksiyon başlatıcısı tarafından gereken parametreleri alan adlı bir genişletme yöntemi ekleyebilirsiniz. Genel Koleksiyonlar için koleksiyon başlatıcıları kullandığınızda bu genellikle yapmanız gereken şeydir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Collections.Generic.List%601> bir koleksiyon başlatıcısının tür nesneleri eklemek için kullanılabilmesi için genel türe bir genişletme yönteminin nasıl ekleneceğini gösterir `Employee` . Genişletme yöntemi, kısaltılmış koleksiyon başlatıcısı sözdizimini kullanmanıza olanak sağlar.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon Başlatıcıları](index.md)
- [Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma](how-to-create-a-collection-used-by-a-collection-initializer.md)
