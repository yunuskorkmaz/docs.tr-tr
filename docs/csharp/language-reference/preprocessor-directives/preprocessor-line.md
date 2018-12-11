---
title: '#Satır - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 5933cf04a3fc8a1e986bff95ad1f38481883a340
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245003"
---
# <a name="line-c-reference"></a>#line (C# Başvurusu)
`#line` Derleyicinin değiştirmenize olanak tanır satır numaraları ve (isteğe bağlı olarak) hataları ve uyarıları için dosya adı çıktı.

Aşağıdaki örnek, iki uyarı satır numaraları ile ilişkili rapor gösterilmektedir. `#line 200` Yönergesi, sonraki satırın numarasını (varsayılan #6 olmasına rağmen) 200 olmasını zorlar ve sonraki #line yönergesi kadar dosya adı "Özel" raporlanır. #Line varsayılan yönergesi, önceki yönerge tarafından yeniden numaralandırılır satırları sayar kendi varsayılan numaralandırma için satır numaralandırmasını döndürür.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;
        int j;
#line default  
        char c;
        float f;
#line hidden // numbering not affected  
        string s;   
        double d;
    }  
}  
```  
Derleme aşağıdaki çıktıyı üretir:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Açıklamalar  
 `#line` Yönergesi bir derleme işlemi otomatik, ara adım modunda kullanılabilir. Örneğin, satırları, özgün kaynak kodu dosyasından kaldırıldı, ancak derleyicinin, çıkış dosyasında numaralandırma orijinal satıra göre hala istiyordu, satırları kaldırın ve ardından özgün satır ile numaralandırma benzetimini `#line`.  
  
 `#line hidden` Yönergesi gizler, hata ayıklayıcı art arda gelen satırlar kod Geliştirici adımlar, tüm satırlar arasında olacak şekilde bir `#line hidden` ve sonraki `#line` yönergesi (varsayarak değil başka bir `#line hidden` yönergesi) üzerinden basamaklı. Bu seçenek, kullanıcı tanımlı ve makine tarafından üretilen kod arasında ayırt etmek ASP.NET izin vermek için de kullanılabilir. ASP.NET bu özelliği birincil kullanıcısı olsa da, daha fazla kaynak oluşturucuları hale getirecek bunu kullanmaya olasıdır.  
  
 A `#line hidden` yönergesi dosya adları etkilemez veya satır numaraları hatası raporlama. Diğer bir deyişle, gizli bir bloğu içinde bir hatayla karşılaşılırsa, derleyici geçerli dosya adı ve satır sayısı hata rapor eder.  
  
 `#line filename` Yönergesi derleyici çıktısında görüntülenmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak içinde olmalıdır ("") ve satır numarasıyla gelmelidir.  
  
 Bir kaynak kodu dosyası herhangi bir sayıda olabilir `#line` yönergeleri.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek, hata ayıklayıcı gizli kod satırları nasıl yoksayar gösterir. Örneği çalıştırdığınızda, üç metin satırlarını görüntüler. Ancak, örnekte gösterildiği gibi bir kesme noktası ayarlayın ve kodunuz içinde adım adım F10 isabet, hata ayıklayıcı'nın gizli çizgi yok sayar göreceksiniz. Ayrıca gizli satırında bir kesme noktası ayarlasanız bile hata ayıklayıcı hala yok, dikkat edin.  
  
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

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
