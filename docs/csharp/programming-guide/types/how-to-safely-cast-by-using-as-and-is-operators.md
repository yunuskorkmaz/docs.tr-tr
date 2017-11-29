---
title: "Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)
Nesneler biçimli olduğundan türetilmiş bir tür tutmak için bir temel sınıf türünde bir değişken için mümkündür. Türetilen türün yöntemi erişmek için türetilmiş bir tür değerine geri dönüştürmek gereklidir. Ancak, basit bir girişiminde atma riskini bu gibi durumlarda cast oluşturur bir <xref:System.InvalidCastException>. Diğer bir deyişle neden C# sağlar [olan](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) işleçler. Bir özel durum oluşturulmasına neden olmadan bir cast başarılı olup olmadığını sınamak için aşağıdaki işleçleri kullanabilirsiniz. Genel olarak, `as` işleci olduğundan daha verimli cast başarıyla yapılabilmesi için gerçekten cast değeri döndürür. `is` İşleci bir Boole değeri döndürür. Bu nedenle yalnızca bir nesnenin türünü belirlemek istiyorsanız ancak aslında cast gerekmez kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler nasıl kullanılacağını `is` ve `as` başka bir özel durum atma riski olmadan için bir başvuru cast işleçleri yazın. Bu örnek ayrıca nasıl kullanılacağını gösterir `as` boş değer atanabilen değer türleri olan işleci.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [Atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)
