---
title: '#çizgi - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712500"
---
# <a name="line-c-reference"></a>#line (C# Başvurusu)

`#line`hatalar ve uyarılar için derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) dosya adı çıktısını değiştirmenizi sağlar.

Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarının nasıl raporedilen gösteriş olduğunu gösterir. Yönerge, `#line 200` bir sonraki satırın numarasını 200 olmaya zorlar (varsayılan `#line` #6 olmasına rağmen) ve bir sonraki yönergeye kadar dosya adı "Özel" olarak bildirilir. Yönerge, `#line default` satır numarasını varsayılan numaralandırmasına döndürür ve bu satırlar önceki yönerge tarafından yeniden numaralandırılır.

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

Yönerge, `#line` yapı işleminde otomatik, ara adımda kullanılabilir. Örneğin, satırlar özgün kaynak kodu dosyasından kaldırıldıysa, ancak yine de derleyicinin dosyadaki özgün satır numaralandırmasına dayalı çıktı oluşturmasını istediyseniz, satırları kaldırabilir ve özgün satır numaralandırmasını simüle `#line`edebilirsiniz.

Yönerge, `#line hidden` geliştirici kod boyunca adım attığında, a `#line hidden` ve sonraki `#line` yönerge arasındaki tüm satırların (başka bir `#line hidden` yönerge olmadığını varsayarak) üzerine adım atacağı şekilde, ardışık satırları hata ayıklayıcıdan gizler. Bu seçenek, ASP.NET kullanıcı tanımlı ve makine tarafından oluşturulan kod arasında ayrım yapmak için de kullanılabilir. ASP.NET bu özelliğin birincil tüketici olmasına rağmen, daha fazla kaynak jeneratörleri bunu kullanmak olasıdır.

Yönerge, `#line hidden` hata bildiriminde dosya adlarını veya satır numaralarını etkilemez. Diğer bir deyişle, gizli bir blokta bir hatayla karşılaşılırsa, derleyici geçerli dosya adını ve hatanın satır numarasını bildirir.

Yönerge, `#line filename` derleyici çıktısında görünmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak işaretleri ("") olmalıdır ve bir satır numarası önce olmalıdır.

Kaynak kod dosyasında `#line` herhangi bir sayıda yönerge olabilir.

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, hata ayıklayıcının koddaki gizli satırları nasıl yoksaydığını gösterir. Örneği çalıştırdığınızda, üç metin satırı görüntülenir. Ancak, örnekte gösterildiği gibi bir kesme noktası ayarladığınızda ve kodu geçmek için F10 tuşuna bastığınızda, hata ayıklayıcının gizli satırı yok saydığını fark esiniz. Gizli çizgide bir kesme noktası ayarlasanız bile hata ayıklamanın yine de yok sayacağına dikkat edin.

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

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
