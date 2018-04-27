---
title: 'Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesneleri Başlatma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8e9130983aabe991660ff4cca90b33609f86c158
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesneleri Başlatma (C# Programlama Kılavuzu)
Nesne başlatıcıları türde nesne türü için bir oluşturucu açıkça çağırmadan bildirim temelli bir şekilde başlatmak için kullanabilirsiniz.  
  
 Aşağıdaki örnekler nesne başlatıcıları adlandırılmış nesnelerinin ile nasıl kullanılacağını gösterir. Derleyici işlemleri başlatıcıları ilk varsayılan örnek oluşturucusu erişme ve üye başlatmaları işleme nesne. Bu nedenle, varsayılan oluşturucu olarak bildirilirse `private` sınıfında genel erişim gerektiren nesne başlatıcıları başarısız olur.  
  
 Anonim bir tür tanımlanıyorsa nesne Başlatıcı kullanmanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: dönüş alt öğesi özelliklerin sorguda](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir başlatma gösterilmektedir `StudentName` nesne başlatıcıları kullanarak türü.  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyonu başlatmak gösterilmiştir `StudentName` koleksiyon Başlatıcısı kullanarak türleri. Koleksiyon başlatıcısı bir dizi virgülle ayrılmış nesne başlatıcıları olduğuna dikkat edin.  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
