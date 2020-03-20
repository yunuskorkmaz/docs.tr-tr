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
# <a name="expressions"></a><span data-ttu-id="b073a-102">İfadeler</span><span class="sxs-lookup"><span data-stu-id="b073a-102">Expressions</span></span>

<span data-ttu-id="b073a-103">Windows İş Akışı Temeli (WF) ifadesi, sonucu döndüren herhangi bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="b073a-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="b073a-104">Tüm ifade etkinlikleri dolaylı <xref:System.Activities.Activity%601>olarak, etkinliğin <xref:System.Activities.OutArgument> geri <xref:System.Activities.Activity%601.Result%2A> dönüş değeri olarak adlandırılan bir özelliği içeren türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b073a-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="b073a-105">gibi <xref:System.Activities.Expressions.VariableValue%601> basit olanlardan ve <xref:System.Activities.Expressions.VariableReference%601>operatör faaliyetleri aracılığıyla tek iş akışı değişkenine erişim sağlayan, karmaşık <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> etkinliklere kadar çok çeşitli ifade etkinliklerine sahip gemiler, sonucu üretmek için Visual Basic dilinin tam genişliğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b073a-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="b073a-106">Ek ifade etkinlikleri türeyen <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="b073a-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="b073a-107">İfadeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="b073a-107">Using Expressions</span></span>
 <span data-ttu-id="b073a-108">İş akışı <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tasarımcısı <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> Visual Basic projelerindeki tüm <xref:Microsoft.CSharp.Activities.CSharpValue%601> ifadeleri <xref:Microsoft.CSharp.Activities.CSharpReference%601> ve C# iş akışı projelerindeki ifadeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b073a-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="b073a-109">.NET Framework 4.5'te iş akışı projelerinde C# ifadeleri desteği tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="b073a-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="b073a-110">Daha fazla bilgi için [C# İfadeleri'ne](csharp-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b073a-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="b073a-111">Tasarımcı tarafından üretilen iş akışları, aşağıdaki örnekte olduğu gibi ifadelerin kare parantez içinde göründüğü XAML'ye kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="b073a-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

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

 <span data-ttu-id="b073a-112">Kodda bir iş akışı tanımlanırken, herhangi bir ifade etkinlikleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b073a-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="b073a-113">Aşağıdaki örnek, üç sayı eklemek için işleç etkinlikleri nin bir bileşiminin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b073a-113">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

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

 <span data-ttu-id="b073a-114">Aynı iş akışı, aşağıdaki örnekte gösterildiği gibi C# lambda ifadeleri kullanılarak daha kompakt bir şekilde ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="b073a-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="b073a-115">Özel İfade Etkinlikleri ile Kullanılabilir İfadeleri Genişletme</span><span class="sxs-lookup"><span data-stu-id="b073a-115">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="b073a-116">İfadeler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ek ifade etkinlikleri oluşturulmasına izin genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="b073a-116">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="b073a-117">Aşağıdaki örnek, üç tamsayı değerlerinin toplamını döndüren bir etkinlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="b073a-117">The following example shows an activity that returns a sum of three integer values.</span></span>

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

 <span data-ttu-id="b073a-118">Bu yeni etkinlikle, aşağıdaki örnekte gösterildiği gibi üç değer eklenen önceki iş akışını yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b073a-118">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

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

 <span data-ttu-id="b073a-119">Koddaki ifadeleri kullanma hakkında daha fazla bilgi için [bkz.](authoring-workflows-activities-and-expressions-using-imperative-code.md)</span><span class="sxs-lookup"><span data-stu-id="b073a-119">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
