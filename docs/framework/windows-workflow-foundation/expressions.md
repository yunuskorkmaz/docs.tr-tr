---
title: İfadeler-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 93d437ae6d20f5d31d80ef3a40f409c589ae084e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962413"
---
# <a name="expressions"></a>İfadeler
Windows Workflow Foundation (WF) ifadesi bir sonuç döndüren etkinliktür. Tüm ifade etkinlikleri, etkinliğin dönüş <xref:System.Activities.Activity%601>değeri olarak adlandırılan <xref:System.Activities.Activity%601.Result%2A> bir <xref:System.Activities.OutArgument> özelliği içeren öğesinden dolaylı olarak türetilir. [!INCLUDE[wf1](../../../includes/wf1-md.md)], ve gibi basit <xref:System.Activities.Expressions.VariableValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> etkinliklerden tek iş akışı değişkenine erişim sağlayan ve gibi karmaşık etkinliklere ve bu teklif <xref:System.Activities.Expressions.VariableReference%601> sonucu oluşturmak için Visual Basic dilinin tam enine erişin. <xref:System.Activities.CodeActivity%601> Veya<xref:System.Activities.NativeActivity%601>' den türeterek ek ifade etkinlikleri oluşturulabilir.  
  
## <a name="using-expressions"></a>Ifadeleri kullanma  
 Workflow Designer, <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.CSharp.Activities.CSharpValue%601> C# Visual Basic projelerindeki tüm ifadeler ve iş akışı projelerindeki ifadeler için kullanır. <xref:Microsoft.CSharp.Activities.CSharpReference%601>  
  
> [!NOTE]
> .NET Framework 4,5 C# ' de iş akışı projelerindeki ifadeler için destek eklenmiştir. Daha fazla bilgi için bkz [ C# . ifadeler](csharp-expressions.md).  
  
 Tasarımcı tarafından üretilen iş akışları, aşağıdaki örnekte olduğu gibi, ifadelerin köşeli ayraç içinde göründüğü XAML 'ye kaydedilir.  
  
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
  
 Kodda bir iş akışı tanımlarken, herhangi bir ifade etkinliği kullanılabilir. Aşağıdaki örnek, üç sayı eklemek için işleç etkinliklerini bir bileşim kullanımını gösterir.  
  
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
  
 Aynı iş akışı, aşağıdaki örnekte gösterildiği gibi lambda ifadeleri C# kullanılarak daha sıkı ifade edilebilir.  
  
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
  
 Aşağıdaki örnekte gösterildiği gibi, iş akışı Visual Basic ifade etkinlikleri kullanılarak da ifade edilebilir.  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Özel Ifade etkinlikleriyle kullanılabilir Ifadeleri genişletme  
 İçindeki [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ifadeler, ek ifade etkinliklerinin oluşturulmasını sağlayan genişletilebilir. Aşağıdaki örnek, üç tamsayı değerinin toplamını döndüren bir etkinliği gösterir.  
  
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
  
 Bu yeni etkinlikle, aşağıdaki örnekte gösterildiği gibi üç değer ekleyen önceki iş akışını yeniden yazabilirsiniz.  
  
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
  
 Koddaki ifadeleri kullanma hakkında daha fazla bilgi için, bkz. [using Iş akışları, etkinlikler ve ifadeleri, zorunlu kod kullanarak yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).
