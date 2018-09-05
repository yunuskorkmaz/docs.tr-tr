---
title: Özel türler ile Switch etkinliği kullanımı
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535445"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Özel türler ile Switch etkinliği kullanımı
Bu örnek nasıl etkinleştireceğiniz anlatılmaktadır bir <xref:System.Activities.Statements.Switch%601> çalışma zamanında kullanıcı tarafından tanımlanan karmaşık tür değerlendirmek için etkinlik. Çoğu geleneksel yordamsal programlama dillerinde, bir [geçiş](https://go.microsoft.com/fwlink/?LinkId=180521) deyimi bir yürütme mantığı bir değişkenin koşullu değerlendirmeye göre seçer. Geleneksel olarak, bir `switch` deyimi, statik olarak değerlendirilen bir ifade üzerinde çalışır. Örneğin, C# ' de, yalnızca temel türler, gibi başka bir deyişle <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, ve sabit listesi türleri desteklenir.  
  
 Özel bir sınıf geçişi etkinleştirmek için mantıksal çalışma zamanında özel karmaşık türün değerlerini değerlendirmek için uygulanmalıdır. Bu örnek adlı bir özel karmaşık türde değiştirme olanağı tanıma gösterir `Person`.  
  
-   Özel bir sınıf içinde `Person`, <xref:System.ComponentModel.TypeConverter> özniteliği özel adı ile bildirilen <xref:System.ComponentModel.TypeConverter>.  
  
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
  
-   Özel bir <xref:System.ComponentModel.TypeConverter> sınıfı bir dize ve özel bir sınıf örneği için bir dize özel bir sınıf örneği dönüştürme gerçekleştiren uygulanır.  
  
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
  
 Bu örnekte aşağıdaki dosyalar dahildir:  
  
-   **Person.cs**: tanımlar `Person` sınıfı.  
  
-   **PersonConverter.cs**: tür dönüştürücü `Person` sınıfı.  
  
-   **Sequence.XAML**: geçer üzerinden bir iş akışı `Person` türü.  
  
-   **Program.cs**: iş akışını çalıştıran ana işlevi.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  İçinde Switch.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Örneği çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerleşik Etkinlik Kitaplığı](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
