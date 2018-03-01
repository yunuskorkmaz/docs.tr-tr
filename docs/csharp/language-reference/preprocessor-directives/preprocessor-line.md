---
title: "#satır (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d2f42915d214349eebff40949482d7f603c0c2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="line-c-reference"></a>#line (C# Başvurusu)
`#line`Derleyicinin satır numarasını ve (isteğe bağlı) hataları ve uyarıları için dosya adı çıktı değiştirmenize olanak tanır. Bu örnekte, iki uyarıları satır numaralarını ile ilişkili rapor gösterilmektedir. `#line 200` Yönergesi zorlar (varsayılan #7 olmasına rağmen) 200 satır numarasını ve sonraki #line yönergesi kadar dosya adı "Özel" olarak raporlanır. #Line varsayılan yönergesi önceki yönergesi tarafından yeniden numaralandırılır satırları sayar kendi varsayılan numaralandırma için numaralandırma satır döndürür.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `#line` Yönergesi derleme sürecindeki otomatik, Ara bir adımda kullanılabilir. Örneğin, satırları özgün kaynak kodu dosyasından kaldırıldı, ancak hala özgün satır dosyasında numaralandırmasını göre çıktı üretmek için derleyici istedi, size satırları kaldırın ve özgün satır ile numaralandırma benzetimini `#line`.  
  
 `#line hidden` Yönergesi gizler hata ayıklayıcı art arda gelen satırlardan sağlayacak şekilde Geliştirici koduyla adımlar, tüm satırları arasında bir `#line hidden` ve sonraki `#line` yönergesi (varsayılarak olmayan başka bir `#line hidden` yönergesi) üzerinden adım adım. Bu seçenek, kullanıcı tanımlı ve makine oluşturulan kod arasında ayırt etmek ASP.NET izin vermek için de kullanılabilir. ASP.NET bu özelliğin birincil tüketici olsa da, daha fazla kaynak oluşturucuları yapacak bunu kullanmak olasıdır.  
  
 A `#line hidden` yönergesi dosya adlarını etkilemez veya satır numaraları hata raporlama. Diğer bir deyişle, gizli bir bloğunda hatayla karşılaşılırsa, derleyici geçerli dosya adı ve satır numarası hata bildirir.  
  
 `#line filename` Yönergesi derleyici çıktısında görüntülenmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak işaretleri içinde olmalıdır ("") ve bir satır sayısı tarafından gelmelidir.  
  
 Kaynak kodu dosyasının herhangi bir sayıda olabilir `#line` yönergeleri.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek kodda gizli satırlar hata ayıklayıcı nasıl yoksayar gösterir. Örnek çalıştırdığınızda, üç satırlık metin görüntüler. Ancak, örnekte gösterildiği gibi bir kesme noktası ayarlayın ve kod üzerinden adım F10 isabet zaman hata ayıklayıcı gizli çizgi yoksayar fark edersiniz. Ayrıca gizli satırında bir kesme noktası ayarlasanız bile hata ayıklayıcı hala bunu göz ardı eder dikkat edin.  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
