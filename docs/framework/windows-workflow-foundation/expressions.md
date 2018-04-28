---
title: Expressions1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18c64daca1532bb626a59e5f01528e207e6b6b87
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="expressions"></a>İfadeler
Bir sonuç döndürür herhangi bir etkinliği bir Windows Workflow Foundation (WF) ifadesidir. Tüm ifade etkinlikleri dolaylı olarak türetilen <xref:System.Activities.Activity%601>, içeren bir <xref:System.Activities.OutArgument> adlı özellik <xref:System.Activities.Activity%601.Result%2A> etkinliğin dönüş değeri olarak. [!INCLUDE[wf1](../../../includes/wf1-md.md)] çok çeşitli ifade etkinlikleri olanları gibi basit gelir <xref:System.Activities.Expressions.VariableValue%601> ve <xref:System.Activities.Expressions.VariableReference%601>, gibi tek bir iş akışı değişken karmaşık etkinliklere işleci etkinlikleri üzerinden erişim sağlayan <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Bu teklif sonucu oluşturmak için Visual Basic dil için olan tüm tekliflerden erişin. Ek ifade etkinlikleri türetme tarafından oluşturulabilir <xref:System.Activities.CodeActivity%601> veya <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>İfadeler kullanma  
 İş Akışı Tasarımcısı kullanır <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> tüm ifadelerde Visual Basic projeleri için ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve <xref:Microsoft.CSharp.Activities.CSharpReference%601> ifadeleri iş akışı C# projelerinde için.  
  
> [!NOTE]
>  C# ifadeleri iş akışı projelerinde desteği sunulmuştur [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Daha fazla bilgi için bkz: [C# ifadeleri](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
 Tasarımcı tarafından üretilen iş akışları ifadeleri aşağıdaki örnekteki gibi köşeli ayraçlar içinde çevrelenmiş göründüğü XAML'de kaydedilir.  
  
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
  
 Bir iş akışı kodda tanımlarken ifade etkinlikler kullanılabilir. Aşağıdaki örnek bir birleşim işleci etkinliklerin üç sayıları kullanımını gösterir.  
  
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
  
 Aynı iş akışı C# lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi kullanarak daha sıkı şekilde ifade edilebilir.  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Kullanılabilir özel ifade etkinlikleri ifadelerle genişletme  
 İfadelerde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ek ifade etkinlikleri oluşturulmasına izin vererek genişletilebilir. Aşağıdaki örnekte, üç tamsayı değerlerin toplamını döndürür bir etkinlik gösterir.  
  
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
  
 Bu yeni aktivitesi aşağıdaki örnekte gösterildiği gibi üç değerden eklenen önceki bir iş akışı yazabilirsiniz.  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] ifadeler kod içinde kullanma, bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).
