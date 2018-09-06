---
title: Özel türler ile Switch etkinliği kullanımı
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038880"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="45266-102">Özel türler ile Switch etkinliği kullanımı</span><span class="sxs-lookup"><span data-stu-id="45266-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="45266-103">Bu örnek nasıl etkinleştireceğiniz anlatılmaktadır bir <xref:System.Activities.Statements.Switch%601> çalışma zamanında kullanıcı tarafından tanımlanan karmaşık tür değerlendirmek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="45266-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="45266-104">Çoğu geleneksel yordamsal programlama dillerinde, bir [geçiş](https://go.microsoft.com/fwlink/?LinkId=180521) deyimi bir yürütme mantığı bir değişkenin koşullu değerlendirmeye göre seçer.</span><span class="sxs-lookup"><span data-stu-id="45266-104">In most traditional procedural programming languages, a [switch](https://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="45266-105">Geleneksel olarak, bir `switch` deyimi, statik olarak değerlendirilen bir ifade üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="45266-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="45266-106">Örneğin, C# ' de, yalnızca temel türler, gibi başka bir deyişle <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, ve sabit listesi türleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="45266-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="45266-107">Özel bir sınıf geçişi etkinleştirmek için mantıksal çalışma zamanında özel karmaşık türün değerlerini değerlendirmek için uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45266-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="45266-108">Bu örnek adlı bir özel karmaşık türde değiştirme olanağı tanıma gösterir `Person`.</span><span class="sxs-lookup"><span data-stu-id="45266-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="45266-109">Özel bir sınıf içinde `Person`, <xref:System.ComponentModel.TypeConverter> özniteliği özel adı ile bildirilen <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="45266-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="45266-110">Özel bir sınıf içinde `Person`, <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> sınıfları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="45266-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
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
  
-   <span data-ttu-id="45266-111">Özel bir <xref:System.ComponentModel.TypeConverter> sınıfı bir dize ve özel bir sınıf örneği için bir dize özel bir sınıf örneği dönüştürme gerçekleştiren uygulanır.</span><span class="sxs-lookup"><span data-stu-id="45266-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
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
  
 <span data-ttu-id="45266-112">Bu örnekte aşağıdaki dosyalar dahildir:</span><span class="sxs-lookup"><span data-stu-id="45266-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="45266-113">**Person.cs**: tanımlar `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45266-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="45266-114">**PersonConverter.cs**: tür dönüştürücü `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45266-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="45266-115">**Sequence.XAML**: geçer üzerinden bir iş akışı `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="45266-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="45266-116">**Program.cs**: iş akışını çalıştıran ana işlevi.</span><span class="sxs-lookup"><span data-stu-id="45266-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="45266-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="45266-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="45266-118">İçinde Switch.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45266-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="45266-119">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="45266-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="45266-120">Örneği çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="45266-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45266-121">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="45266-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45266-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="45266-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45266-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="45266-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45266-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="45266-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="45266-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45266-125">See Also</span></span>  
 [<span data-ttu-id="45266-126">Yerleşik Etkinlik Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="45266-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
