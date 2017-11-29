---
title: "Nasıl yapılır: Dize İçeriklerini Değiştirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>Nasıl yapılır: Dize İçeriklerini Değiştirme (C# Programlama Kılavuzu)
Dizeleri olduğundan *değişmez*, (güvenli olmayan kod kullanmadan) mümkün değildir oluşturulduktan sonra bir dize nesnesi değerini değiştirmek için. Ancak, bir dize değerini değiştirin ve yeni bir dize nesnesi sonucu depolamak için birçok yolu vardır. <xref:System.String?displayProperty=nameWithType> SAX bir giriş, çalışan yöntemleri dize ve yeni bir dize nesnesi döndürür. Çoğu durumda, yeni nesne özgün dizeye tutulan değişkenine atayabilirsiniz. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Sınıfı, benzer bir şekilde iş ek yöntemleri sağlar. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Sınıfı sağlar değiştirebileceğiniz bir karakter arabellek "yerinde." Çağırmanız <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> arabellek geçerli içeriğini içeren yeni bir dize nesnesi oluşturmak için yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, değiştirmek veya alt dizeler belirtilen dizede kaldırmak için çeşitli yollar gösterir.  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>Örnek  
 Dizi gösterim biçimini kullanarak bir dizedeki karakterleri tek tek erişmek için kullanabileceğiniz <xref:System.Text.StringBuilder> overloads nesne `[]` iç karakter arabelleğini erişim sağlamak için işleci. Kullanarak bir karakter dizisi için dize dönüştürebilirsiniz <xref:System.String.ToCharArray%2A> yöntemi. Aşağıdaki örnek kullanır `ToCharArray` dizi oluşturmak için. Bazı öğeler bu dizinin sonra değiştirilir. Bir char alan bir dize Oluşturucu giriş parametresi olarak dizi sonra yeni bir dize oluşturmak için çağrılır.  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek C tarzı char dizileri için benzer bir şekilde güvenli olmayan kod kullanarak bir dize yerinde değiştirmek isteyebilirsiniz bu çok nadir durumlarda sağlanır. Örnek fixed anahtar sözcüğünü kullanarak tek tek karakterleri "yerinde" erişmek nasıl gösterir. Ayrıca, bir olası yan C# Derleyici (Stajyer) dizeleri dahili olarak depolar şekilde sonucu etkisi dizelerde güvensiz işlemleri gösterir. Genel olarak, kesinlikle gerekli olmadığı sürece bu teknik kullanmamanız gerekir.  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)
