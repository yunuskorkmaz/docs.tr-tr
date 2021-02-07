---
description: 'Daha fazla bilgi edinin: Ifadeler'
title: İfadeler-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: de16168585e2bbcbf8251c8e4b7c06784d72859d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742361"
---
# <a name="expressions"></a><span data-ttu-id="40075-103">İfadeler</span><span class="sxs-lookup"><span data-stu-id="40075-103">Expressions</span></span>

<span data-ttu-id="40075-104">Windows Workflow Foundation (WF) ifadesi bir sonuç döndüren etkinliktür.</span><span class="sxs-lookup"><span data-stu-id="40075-104">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="40075-105">Tüm ifade etkinlikleri <xref:System.Activities.Activity%601> , <xref:System.Activities.OutArgument> <xref:System.Activities.Activity%601.Result%2A> etkinliğin dönüş değeri olarak adlandırılan bir özelliği içeren öğesinden dolaylı olarak türetilir.</span><span class="sxs-lookup"><span data-stu-id="40075-105">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="40075-106"><xref:System.Activities.Expressions.VariableValue%601>, ve gibi basit <xref:System.Activities.Expressions.VariableReference%601> etkinliklerden tek bir iş akışı değişkenine erişim sağlayan ve gibi karmaşık etkinliklere, <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> sonucu oluşturmak için Visual Basic dilin tam enine erişim sağlayan çok sayıda ifade etkinlikleriyle birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="40075-106">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="40075-107">Veya ' den türeterek ek ifade etkinlikleri oluşturulabilir <xref:System.Activities.CodeActivity%601> <xref:System.Activities.NativeActivity%601> .</span><span class="sxs-lookup"><span data-stu-id="40075-107">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="40075-108">Ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="40075-108">Using Expressions</span></span>

 <span data-ttu-id="40075-109">Workflow Designer <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> , Visual Basic projelerindeki tüm ifadeler ve ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.CSharp.Activities.CSharpReference%601> C# iş akışı projelerindeki ifadeler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="40075-109">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="40075-110">İş akışı projelerinde C# ifadeleri için destek .NET Framework 4,5 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="40075-110">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="40075-111">Daha fazla bilgi için bkz. [C# ifadeleri](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="40075-111">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="40075-112">Tasarımcı tarafından üretilen iş akışları, aşağıdaki örnekte olduğu gibi, ifadelerin köşeli ayraç içinde göründüğü XAML 'ye kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="40075-112">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

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

 <span data-ttu-id="40075-113">Kodda bir iş akışı tanımlarken, herhangi bir ifade etkinliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40075-113">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="40075-114">Aşağıdaki örnek, üç sayı eklemek için işleç etkinliklerinin bir bileşim kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="40075-114">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

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

 <span data-ttu-id="40075-115">Aşağıdaki örnekte gösterildiği gibi C# lambda ifadeleri kullanılarak aynı iş akışı daha sıkı ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="40075-115">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="40075-116">Özel Ifade etkinlikleriyle kullanılabilir Ifadeleri genişletme</span><span class="sxs-lookup"><span data-stu-id="40075-116">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="40075-117">İçindeki ifadeler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] , ek ifade etkinliklerinin oluşturulmasını sağlayan genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="40075-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="40075-118">Aşağıdaki örnek, üç tamsayı değerinin toplamını döndüren bir etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="40075-118">The following example shows an activity that returns a sum of three integer values.</span></span>

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

 <span data-ttu-id="40075-119">Bu yeni etkinlikle, aşağıdaki örnekte gösterildiği gibi üç değer ekleyen önceki iş akışını yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40075-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

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

 <span data-ttu-id="40075-120">Koddaki ifadeleri kullanma hakkında daha fazla bilgi için, bkz. [using Iş akışları, etkinlikler ve ifadeleri, zorunlu kod kullanarak yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="40075-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
