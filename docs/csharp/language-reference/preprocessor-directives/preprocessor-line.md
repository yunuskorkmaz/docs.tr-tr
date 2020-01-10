---
title: '#satır C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712500"
---
# <a name="line-c-reference"></a>#line (C# Başvurusu)

`#line`, derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) dosya adı çıktısını hatalar ve uyarılar için değiştirmenize olanak sağlar.

Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir. `#line 200` yönergesi sonraki satırın numarasını 200 olarak zorlar (varsayılan değer #6 olur) ve sonraki `#line` yönergesine kadar dosya adı "özel" olarak raporlanır. `#line default` yönergesi, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmaya satır numaralandırmayı döndürür.

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

`#line` yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir. Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından `#line`orijinal satır numaralandırmasının benzetimini yapabilirsiniz.

`#line hidden` yönergesi, hata ayıklayıcıdan ardışık satırları gizler, örneğin, geliştirici kodda, bir `#line hidden` ve bir sonraki `#line` yönergesi arasındaki herhangi bir satır (başka bir `#line hidden` yönergesi olmadığı varsayılırsa), bu yana bir adım daha alınır. Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir. ASP.NET bu özelliğin birincil tüketicisi olsa da, büyük olasılıkla daha fazla kaynak oluşturanlar bunu kullanacaktır.

`#line hidden` yönergesi, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez. Diğer bir deyişle, gizli bir blokta bir hata ile karşılaşılırsa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.

`#line filename` yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.

Kaynak kodu dosyasında herhangi bir sayıda `#line` yönergesi olabilir.

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
