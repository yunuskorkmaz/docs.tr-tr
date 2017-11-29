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
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Özel türler anahtar etkinlikle kullanımı
Bu örnek nasıl etkinleştirileceğini açıklar bir <!--zz <xref:System.Activities. Statements.Switch`1>--> `xref:System.Activities` Statements.Switch`1?qualifyHint=False&autoUpgrade=True activity to evaluate a user-defined complex type at runtime. In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable. Traditionally, a `geçiş ' deyimi statik olarak değerlendirilen bir ifade üzerinde çalışır. Örneğin, C# gibi yalnızca basit türler yani <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, ve Numaralandırma türleri desteklenir.  
  
 Özel bir sınıf değiştirmeyi etkinleştirmek için mantığı çalışma zamanında özel karmaşık türün değerlerini değerlendirmek için uygulanmalıdır. Bu örnek adlı bir özel karmaşık tür üzerinde değiştirmeyi etkinleştirmek gösterilmiştir `Person`.  
  
-   Özel bir sınıf içinde `Person`, <xref:System.ComponentModel.TypeConverter> özniteliği özel adıyla bildirilen <xref:System.ComponentModel.TypeConverter>.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Özel bir sınıf içinde `Person`, <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> sınıfları geçersiz kılınır.  
  
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
  
-   Özel bir <xref:System.ComponentModel.TypeConverter> sınıfı bir dize ve özel bir sınıf örneği dizeye özel sınıfının bir örneği dönüştürülmesi gerçekleştiren uygulanır.  
  
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
  
 Bu örnekte aşağıdaki dosyaları bulunmaktadır:  
  
-   **Person.cs**: tanımlar `Person` sınıfı.  
  
-   **PersonConverter.cs**: için tür dönüştürücüsünü `Person` sınıfı.  
  
-   **Sequence.XAML**: geçer üzerinden bir iş akışı `Person` türü.  
  
-   **Program.cs**: iş akışı çalıştıran ana işlevi.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  İçinde Switch.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Örneği çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerleşik etkinlik kitaplığı](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
