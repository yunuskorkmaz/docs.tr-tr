---
description: '#Line-C# başvurusu'
title: '#Line-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: e2a5ecb6c29184123b8a88ae1b12caf24ec7296a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138000"
---
# <a name="line-c-reference"></a>#line (C# Başvurusu)

`#line` Derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) hata ve uyarı için dosya adı çıktısını değiştirmenize izin verir.

Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir. `#line 200`Yönerge, sonraki satırın numarasını 200 (varsayılan değer #6) olarak zorlar ve sonraki `#line` yönergeye kadar dosya adı "özel" olarak raporlanır. `#line default`Yönerge, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmayla satır numaralandırmayı döndürür.

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

`#line`Yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir. Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından özgün satır numaralandırmasının benzetimini yapabilirsiniz `#line` .

`#line hidden`Yönerge, hata ayıklayıcıdaki ardışık satırları gizler, örneğin, geliştirici, kod içinde, bir `#line hidden` ve sonraki `#line` yönerge (başka bir yönerge olmadığı varsayılarak) arasındaki herhangi bir satır `#line hidden` üzerinden ele alınacaktır. Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir. ASP.NET bu özelliğin birincil tüketicisi olsa da, büyük olasılıkla daha fazla kaynak oluşturanlar bunu kullanacaktır.

Bir `#line hidden` yönerge, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez. Diğer bir deyişle, gizli bir blokta bir hata ile karşılaşılırsa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.

`#line filename`Yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.

Kaynak kodu dosyası herhangi bir sayıda `#line` yönergeler içerebilir.

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, hata ayıklayıcının koddaki gizli satırları nasıl yoksaydığı gösterilmektedir. Örneği çalıştırdığınızda üç satırlık metin görüntülenir. Ancak, örnekte gösterildiği gibi bir kesme noktası ayarladığınızda ve kodun içinde ilerlemek için F10 'e bastığınızda, hata ayıklayıcının gizli çizgiyi yoksaydığına dikkat edin. Ayrıca, gizli satırda bir kesme noktası ayarlasanız bile hata ayıklayıcının yok saymaya devam ettiğini unutmayın.

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

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
