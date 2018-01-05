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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61485a59ae3af17bef58c0fccbe062c8b9171a34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="6d72f-102">Özel türler anahtar etkinlikle kullanımı</span><span class="sxs-lookup"><span data-stu-id="6d72f-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="6d72f-103">Bu örnek nasıl etkinleştirileceğini açıklar bir <xref:System.Activities.Statements.Switch%601> çalışma zamanında kullanıcı tarafından tanımlanan karmaşık tür değerlendirmek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6d72f-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="6d72f-104">Çoğu geleneksel yordam programlama dillerinde, bir [geçiş](http://go.microsoft.com/fwlink/?LinkId=180521) deyimi bir değişkene koşullu değerlendirmeye dayanarak bir yürütme mantığını seçer.</span><span class="sxs-lookup"><span data-stu-id="6d72f-104">In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="6d72f-105">Geleneksel olarak, bir `switch` deyimi statik olarak değerlendirilen bir ifade üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="6d72f-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="6d72f-106">Örneğin, C# gibi yalnızca basit türler yani <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, ve Numaralandırma türleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6d72f-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="6d72f-107">Özel bir sınıf değiştirmeyi etkinleştirmek için mantığı çalışma zamanında özel karmaşık türün değerlerini değerlendirmek için uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d72f-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="6d72f-108">Bu örnek adlı bir özel karmaşık tür üzerinde değiştirmeyi etkinleştirmek gösterilmiştir `Person`.</span><span class="sxs-lookup"><span data-stu-id="6d72f-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="6d72f-109">Özel bir sınıf içinde `Person`, <xref:System.ComponentModel.TypeConverter> özniteliği özel adıyla bildirilen <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="6d72f-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="6d72f-110">Özel bir sınıf içinde `Person`, <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> sınıfları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="6d72f-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
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
  
-   <span data-ttu-id="6d72f-111">Özel bir <xref:System.ComponentModel.TypeConverter> sınıfı bir dize ve özel bir sınıf örneği dizeye özel sınıfının bir örneği dönüştürülmesi gerçekleştiren uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6d72f-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
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
  
 <span data-ttu-id="6d72f-112">Bu örnekte aşağıdaki dosyaları bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6d72f-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="6d72f-113">**Person.cs**: tanımlar `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6d72f-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="6d72f-114">**PersonConverter.cs**: için tür dönüştürücüsünü `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6d72f-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="6d72f-115">**Sequence.XAML**: geçer üzerinden bir iş akışı `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="6d72f-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="6d72f-116">**Program.cs**: iş akışı çalıştıran ana işlevi.</span><span class="sxs-lookup"><span data-stu-id="6d72f-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6d72f-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6d72f-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="6d72f-118">İçinde Switch.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d72f-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d72f-119">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d72f-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="6d72f-120">Örneği çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d72f-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d72f-121">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d72f-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d72f-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6d72f-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d72f-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6d72f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d72f-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6d72f-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="6d72f-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d72f-125">See Also</span></span>  
 [<span data-ttu-id="6d72f-126">Yerleşik Etkinlik Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6d72f-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
