---
title: '#satır C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608531"
---
# <a name="line-c-reference"></a>#line (C# Başvurusu)

`#line`Derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) hata ve uyarı için dosya adı çıktısını değiştirmenize izin verir.

Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir. Yönerge, sonraki satırın numarasını 200 (varsayılan değer #6) olarak zorlar ve sonraki `#line` yönergeye kadar dosya adı "özel" olarak raporlanır. `#line 200` `#line default` Yönerge, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmayla satır numaralandırmayı döndürür.

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

`#line` Yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir. Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından özgün satır numaralandırmasının `#line`benzetimini yapabilirsiniz.

Yönerge, hata ayıklayıcıdan ardışık satırları gizler, örneğin, Geliştirici kod içinde, bir ve `#line` sonraki yönerge arasındaki herhangi bir `#line hidden` satır (başka bir `#line hidden` yönerge olmadığı varsayılarak) `#line hidden` ele alınacaktır. Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir. ASP.NET bu özelliğin birincil tüketicisi olsa da, büyük olasılıkla daha fazla kaynak oluşturanlar bunu kullanacaktır.

Bir `#line hidden` yönerge, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez. Diğer bir deyişle, gizli bir blokta bir hata ile karşılaşılırsa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.

`#line filename` Yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.

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

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
