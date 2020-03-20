---
title: İfadeler - WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 93fe449e8fa6c50f715d842c2ef6a9ecbd31aff2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182934"
---
# <a name="expressions"></a>İfadeler

Windows İş Akışı Temeli (WF) ifadesi, sonucu döndüren herhangi bir etkinliktir. Tüm ifade etkinlikleri dolaylı <xref:System.Activities.Activity%601>olarak, etkinliğin <xref:System.Activities.OutArgument> geri <xref:System.Activities.Activity%601.Result%2A> dönüş değeri olarak adlandırılan bir özelliği içeren türetilmiştir. [!INCLUDE[wf1](../../../includes/wf1-md.md)]gibi <xref:System.Activities.Expressions.VariableValue%601> basit olanlardan ve <xref:System.Activities.Expressions.VariableReference%601>operatör faaliyetleri aracılığıyla tek iş akışı değişkenine erişim sağlayan, karmaşık <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> etkinliklere kadar çok çeşitli ifade etkinliklerine sahip gemiler, sonucu üretmek için Visual Basic dilinin tam genişliğine erişim sağlar. Ek ifade etkinlikleri türeyen <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>.

## <a name="using-expressions"></a>İfadeleri Kullanma
 İş akışı <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tasarımcısı <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> Visual Basic projelerindeki tüm <xref:Microsoft.CSharp.Activities.CSharpValue%601> ifadeleri <xref:Microsoft.CSharp.Activities.CSharpReference%601> ve C# iş akışı projelerindeki ifadeleri kullanır.

> [!NOTE]
> .NET Framework 4.5'te iş akışı projelerinde C# ifadeleri desteği tanıtıldı. Daha fazla bilgi için [C# İfadeleri'ne](csharp-expressions.md)bakın.

 Tasarımcı tarafından üretilen iş akışları, aşağıdaki örnekte olduğu gibi ifadelerin kare parantez içinde göründüğü XAML'ye kaydedilir.

```xml
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <Sequence.Variables>
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />
  </Sequence.Variables>
  <Assign>
    <Assign.To>
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>
    </Assign.To>
    <Assign.Value>
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>
    </Assign.Value>
  </Assign>
</Sequence>
```

 Kodda bir iş akışı tanımlanırken, herhangi bir ifade etkinlikleri kullanılabilir. Aşağıdaki örnek, üç sayı eklemek için işleç etkinlikleri nin bir bileşiminin kullanımını gösterir:

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new Add<int, int, int> {
                    Left = new Add<int, int, int> {
                        Left = new InArgument<int>(a),
                        Right = new InArgument<int>(b)
                    },
                    Right = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 Aynı iş akışı, aşağıdaki örnekte gösterildiği gibi C# lambda ifadeleri kullanılarak daha kompakt bir şekilde ifade edilebilir:
  
```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))
        }
    }
};
```

## <a name="extending-available-expressions-with-custom-expression-activities"></a>Özel İfade Etkinlikleri ile Kullanılabilir İfadeleri Genişletme

 İfadeler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ek ifade etkinlikleri oluşturulmasına izin genişletilebilir. Aşağıdaki örnek, üç tamsayı değerlerinin toplamını döndüren bir etkinlik gösterir.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Activities;

namespace ExpressionsDemo
{
    public sealed class AddThreeValues : CodeActivity<int>
    {
        public InArgument<int> Value1 { get; set; }
        public InArgument<int> Value2 { get; set; }
        public InArgument<int> Value3 { get; set; }

        protected override int Execute(CodeActivityContext context)
        {
            return Value1.Get(context) +
                   Value2.Get(context) +
                   Value3.Get(context);
        }
    }
}
```

 Bu yeni etkinlikle, aşağıdaki örnekte gösterildiği gibi üç değer eklenen önceki iş akışını yeniden yazabilirsiniz:

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new AddThreeValues() {
                    Value1 = new InArgument<int>(a),
                    Value2 = new InArgument<int>(b),
                    Value3 = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 Koddaki ifadeleri kullanma hakkında daha fazla bilgi için [bkz.](authoring-workflows-activities-and-expressions-using-imperative-code.md)
