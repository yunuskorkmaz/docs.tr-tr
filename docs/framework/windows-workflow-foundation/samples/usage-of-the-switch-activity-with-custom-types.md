---
title: "Özel türler anahtar etkinlikle kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8a4418c582d00f1163305ce5d63c63c198dbc30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="d29dd-102">Özel türler anahtar etkinlikle kullanımı</span><span class="sxs-lookup"><span data-stu-id="d29dd-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="d29dd-103">Bu örnek nasıl etkinleştirileceğini açıklar bir <!--zz <xref:System.Activities. Statements.Switch`1>--> `xref:System.Activities` Statements.Switch`1?qualifyHint=False&autoUpgrade=True activity to evaluate a user-defined complex type at runtime. In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable. Traditionally, a \`geçiş ' deyimi statik olarak değerlendirilen bir ifade üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d29dd-103">This sample describes how to enable a <!--zz <xref:System.Activities. Statements.Switch`1>--> `xref:System.Activities` Statements.Switch`1?qualifyHint=False&autoUpgrade=True activity to evaluate a user-defined complex type at runtime. In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable. Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="d29dd-104">Örneğin, C# gibi yalnızca basit türler yani <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, ve Numaralandırma türleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d29dd-104">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="d29dd-105">Özel bir sınıf değiştirmeyi etkinleştirmek için mantığı çalışma zamanında özel karmaşık türün değerlerini değerlendirmek için uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d29dd-105">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="d29dd-106">Bu örnek adlı bir özel karmaşık tür üzerinde değiştirmeyi etkinleştirmek gösterilmiştir `Person`.</span><span class="sxs-lookup"><span data-stu-id="d29dd-106">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="d29dd-107">Özel bir sınıf içinde `Person`, <xref:System.ComponentModel.TypeConverter> özniteliği özel adıyla bildirilen <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="d29dd-107">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="d29dd-108">Özel bir sınıf içinde `Person`, <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> sınıfları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="d29dd-108">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="d29dd-109">Özel bir <xref:System.ComponentModel.TypeConverter> sınıfı bir dize ve özel bir sınıf örneği dizeye özel sınıfının bir örneği dönüştürülmesi gerçekleştiren uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d29dd-109">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="d29dd-110">Bu örnekte aşağıdaki dosyaları bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="d29dd-110">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="d29dd-111">**Person.cs**: tanımlar `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d29dd-111">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="d29dd-112">**PersonConverter.cs**: için tür dönüştürücüsünü `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d29dd-112">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="d29dd-113">**Sequence.XAML**: geçer üzerinden bir iş akışı `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="d29dd-113">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="d29dd-114">**Program.cs**: iş akışı çalıştıran ana işlevi.</span><span class="sxs-lookup"><span data-stu-id="d29dd-114">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d29dd-115">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d29dd-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="d29dd-116">İçinde Switch.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d29dd-116">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d29dd-117">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d29dd-117">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="d29dd-118">Örneği çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d29dd-118">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d29dd-119">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d29dd-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d29dd-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d29dd-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d29dd-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d29dd-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d29dd-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d29dd-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="d29dd-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d29dd-123">See Also</span></span>  
 [<span data-ttu-id="d29dd-124">Yerleşik etkinlik kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d29dd-124">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
