---
title: İfadeler-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 092272db2f7979cf12917dfe35e116295db79bf3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868891"
---
# <a name="expressions"></a><span data-ttu-id="68818-102">İfadeler</span><span class="sxs-lookup"><span data-stu-id="68818-102">Expressions</span></span>
<span data-ttu-id="68818-103">Windows Workflow Foundation (WF) ifadesi bir sonuç döndüren etkinliktür.</span><span class="sxs-lookup"><span data-stu-id="68818-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="68818-104">Tüm ifade etkinlikleri, etkinliğin dönüş <xref:System.Activities.Activity%601>değeri olarak adlandırılan <xref:System.Activities.Activity%601.Result%2A> bir <xref:System.Activities.OutArgument> özelliği içeren öğesinden dolaylı olarak türetilir.</span><span class="sxs-lookup"><span data-stu-id="68818-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="68818-105">, ve gibi basit <xref:System.Activities.Expressions.VariableValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> etkinliklerden tek iş akışı değişkenine erişim sağlayan ve gibi karmaşık etkinliklere ve bu teklif <xref:System.Activities.Expressions.VariableReference%601> sonucu oluşturmak için Visual Basic dilinin tam enine erişin.</span><span class="sxs-lookup"><span data-stu-id="68818-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="68818-106"><xref:System.Activities.CodeActivity%601> Veya<xref:System.Activities.NativeActivity%601>' den türeterek ek ifade etkinlikleri oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="68818-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="68818-107">Ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="68818-107">Using Expressions</span></span>  
 <span data-ttu-id="68818-108">Workflow Designer, <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.CSharp.Activities.CSharpValue%601> C# Visual Basic projelerindeki tüm ifadeler ve iş akışı projelerindeki ifadeler için kullanır. <xref:Microsoft.CSharp.Activities.CSharpReference%601></span><span class="sxs-lookup"><span data-stu-id="68818-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68818-109">.NET Framework 4,5 C# ' de iş akışı projelerindeki ifadeler için destek eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="68818-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="68818-110">Daha fazla bilgi için bkz [ C# . ifadeler](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="68818-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="68818-111">Tasarımcı tarafından üretilen iş akışları, aşağıdaki örnekte olduğu gibi, ifadelerin köşeli ayraç içinde göründüğü XAML 'ye kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="68818-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="68818-112">Kodda bir iş akışı tanımlarken, herhangi bir ifade etkinliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68818-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="68818-113">Aşağıdaki örnek, üç sayı eklemek için işleç etkinliklerini bir bileşim kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="68818-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
```  
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
  
 <span data-ttu-id="68818-114">Aynı iş akışı, aşağıdaki örnekte gösterildiği gibi lambda ifadeleri C# kullanılarak daha sıkı ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="68818-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="68818-115">Aşağıdaki örnekte gösterildiği gibi, iş akışı Visual Basic ifade etkinlikleri kullanılarak da ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="68818-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```  
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
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="68818-116">Özel Ifade etkinlikleriyle kullanılabilir Ifadeleri genişletme</span><span class="sxs-lookup"><span data-stu-id="68818-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="68818-117">İçindeki [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ifadeler, ek ifade etkinliklerinin oluşturulmasını sağlayan genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="68818-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="68818-118">Aşağıdaki örnek, üç tamsayı değerinin toplamını döndüren bir etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="68818-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
```  
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
  
 <span data-ttu-id="68818-119">Bu yeni etkinlikle, aşağıdaki örnekte gösterildiği gibi üç değer ekleyen önceki iş akışını yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68818-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="68818-120">Koddaki ifadeleri kullanma hakkında daha fazla bilgi için, bkz. [using Iş akışları, etkinlikler ve ifadeleri, zorunlu kod kullanarak yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="68818-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
