---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: koleksiyon başlatıcısı tarafından kullanılan bir uzantı ekleme yöntemi oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 1fbe6f438c4761ae668a6bd6a0a2c38c8efdb439
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475480"
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
