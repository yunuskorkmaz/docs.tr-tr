---
title: Expressions1
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 047f0f5d0214926fde2fe21efd9a24c4b645ed8e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380163"
---
# <a name="expressions"></a><span data-ttu-id="257c1-102">İfadeler</span><span class="sxs-lookup"><span data-stu-id="257c1-102">Expressions</span></span>
<span data-ttu-id="257c1-103">Windows Workflow Foundation (WF) döndüren herhangi bir etkinliği ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="257c1-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="257c1-104">Tüm ifade etkinlikleri dolaylı olarak türetir <xref:System.Activities.Activity%601>, içeren bir <xref:System.Activities.OutArgument> adlı özellik <xref:System.Activities.Activity%601.Result%2A> etkinliğin dönüş değeri olarak.</span><span class="sxs-lookup"><span data-stu-id="257c1-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="257c1-105">çok çeşitli ifade etkinlikleri olanları gibi basit gelir <xref:System.Activities.Expressions.VariableValue%601> ve <xref:System.Activities.Expressions.VariableReference%601>, gibi karmaşık etkinliklere işleci etkinlikleri aracılığıyla tek bir iş akışı değişkenine erişim sağlayan <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> bu teklifi sonucu oluşturmak için Visual Basic dil için olan tüm tekliflerden erişin.</span><span class="sxs-lookup"><span data-stu-id="257c1-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="257c1-106">Ek ifade etkinlikleri türeterek oluşturulabilir <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="257c1-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="257c1-107">İfadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="257c1-107">Using Expressions</span></span>  
 <span data-ttu-id="257c1-108">İş akışı tasarımcısını kullanan <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> Visual Basic projelerinde tüm ifadeler için ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve <xref:Microsoft.CSharp.Activities.CSharpReference%601> ifadelerinde için C# iş akışı projeleri.</span><span class="sxs-lookup"><span data-stu-id="257c1-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="257c1-109">Destek C# ifadeleri iş akışı projeleri .NET Framework 4. 5 ' tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="257c1-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="257c1-110">Daha fazla bilgi için [ C# ifadeleri](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="257c1-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="257c1-111">İfadeler aşağıdaki örnekte olduğu gibi köşeli parantez kapama göründüğü, XAML tasarımcısı tarafından üretilen iş akışları kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="257c1-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="257c1-112">Bir iş akışı kodu tanımlarken, herhangi bir ifade etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="257c1-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="257c1-113">Aşağıdaki örnek, bir birleşim işleci etkinliklerin üç numaralarını eklemek için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="257c1-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
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
  
 <span data-ttu-id="257c1-114">Aynı iş akışının daha sıkı bir şekilde kullanarak ifade edilebilir C# lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="257c1-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="257c1-115">İş akışı de Visual Basic ifade etkinlikleri kullanarak aşağıdaki örnekte gösterildiği gibi ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="257c1-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="257c1-116">Özel ifade etkinlikleri ile kullanılabilen ifadeler genişletme</span><span class="sxs-lookup"><span data-stu-id="257c1-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="257c1-117">İfadelerde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] oluşturulacak ek ifade etkinlikleri için izin verme genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="257c1-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="257c1-118">Aşağıdaki örnek, bir üç tamsayı değerlerinin toplamını döndüren bir etkinlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="257c1-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
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
  
 <span data-ttu-id="257c1-119">Bu yeni etkinlik ile aşağıdaki örnekte gösterildiği gibi üç değerden eklenen önceki bir iş akışı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="257c1-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="257c1-120">Kodda ifadeleri kullanma hakkında daha fazla bilgi için bkz. [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="257c1-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
