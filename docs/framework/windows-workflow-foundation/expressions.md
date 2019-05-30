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
# <a name="expressions"></a>İfadeler
Windows Workflow Foundation (WF) döndüren herhangi bir etkinliği ifadesidir. Tüm ifade etkinlikleri dolaylı olarak türetir <xref:System.Activities.Activity%601>, içeren bir <xref:System.Activities.OutArgument> adlı özellik <xref:System.Activities.Activity%601.Result%2A> etkinliğin dönüş değeri olarak. [!INCLUDE[wf1](../../../includes/wf1-md.md)] çok çeşitli ifade etkinlikleri olanları gibi basit gelir <xref:System.Activities.Expressions.VariableValue%601> ve <xref:System.Activities.Expressions.VariableReference%601>, gibi karmaşık etkinliklere işleci etkinlikleri aracılığıyla tek bir iş akışı değişkenine erişim sağlayan <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> bu teklifi sonucu oluşturmak için Visual Basic dil için olan tüm tekliflerden erişin. Ek ifade etkinlikleri türeterek oluşturulabilir <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>İfadeleri kullanma  
 İş akışı tasarımcısını kullanan <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> Visual Basic projelerinde tüm ifadeler için ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve <xref:Microsoft.CSharp.Activities.CSharpReference%601> ifadelerinde için C# iş akışı projeleri.  
  
> [!NOTE]
>  Destek C# ifadeleri iş akışı projeleri .NET Framework 4. 5 ' tanıtılmıştır. Daha fazla bilgi için [ C# ifadeleri](csharp-expressions.md).  
  
 İfadeler aşağıdaki örnekte olduğu gibi köşeli parantez kapama göründüğü, XAML tasarımcısı tarafından üretilen iş akışları kaydedilir.  
  
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
  
 Bir iş akışı kodu tanımlarken, herhangi bir ifade etkinlik kullanılabilir. Aşağıdaki örnek, bir birleşim işleci etkinliklerin üç numaralarını eklemek için kullanımını gösterir.  
  
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
  
 Aynı iş akışının daha sıkı bir şekilde kullanarak ifade edilebilir C# lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 İş akışı de Visual Basic ifade etkinlikleri kullanarak aşağıdaki örnekte gösterildiği gibi ifade edilebilir.  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Özel ifade etkinlikleri ile kullanılabilen ifadeler genişletme  
 İfadelerde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] oluşturulacak ek ifade etkinlikleri için izin verme genişletilebilir. Aşağıdaki örnek, bir üç tamsayı değerlerinin toplamını döndüren bir etkinlik gösterir.  
  
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
  
 Bu yeni etkinlik ile aşağıdaki örnekte gösterildiği gibi üç değerden eklenen önceki bir iş akışı yazabilirsiniz.  
  
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
  
 Kodda ifadeleri kullanma hakkında daha fazla bilgi için bkz. [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](authoring-workflows-activities-and-expressions-using-imperative-code.md).
