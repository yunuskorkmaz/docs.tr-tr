---
title: DynamicActivity ile çalışma zamanında etkinlik oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: de67fdd71f28bc0f4b16017d253682ca2615f854
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989733"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>DynamicActivity ile çalışma zamanında etkinlik oluşturma
<xref:System.Activities.DynamicActivity>, ortak Oluşturucusu olan somut, mühürlenmiş bir sınıftır. <xref:System.Activities.DynamicActivity>Etkinlik DOM kullanılarak çalışma zamanında etkinlik işlevselliğini birleştirmek için kullanılabilir.  
  
## <a name="dynamicactivity-features"></a>DynamicActivity özellikleri  
 <xref:System.Activities.DynamicActivity>yürütme özelliklerine, bağımsız değişkenlere ve değişkenlere erişebilir, ancak alt etkinliklerin veya izlemenin zamanlanması gibi çalışma zamanı hizmetlerine erişemez.  
  
 En üst düzey özellikler, iş akışı <xref:System.Activities.Argument> nesneleri kullanılarak ayarlanabilir. Kesinlik temelli kodda, bu bağımsız değişkenler CLR özellikleri kullanılarak yeni bir tür üzerinde oluşturulur. XAML 'de, ve `x:Class` `x:Member` etiketleri kullanılarak bildirilmiştir.  
  
 <xref:System.Activities.DynamicActivity> Kullanılarak<xref:System.ComponentModel.ICustomTypeDescriptor>tasarımcı ile arabirim kullanılarak oluşturulan etkinlikler. Tasarımcıda oluşturulan etkinlikler, aşağıdaki yordamda gösterildiği gibi kullanılarak <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>dinamik olarak yüklenebilir.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Zorunlu kod kullanarak çalışma zamanında etkinlik oluşturmak için  
  
1. OpenVisual Studio 2010.  
  
2. **Dosya**, **Yeni**, **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#**  altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **sıralı Iş akışı konsol uygulaması** ' nı seçin. Yeni projeyi DynamicActivitySample olarak adlandırın.  
  
3. Merhaba etkinlik projesinde Workflow1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.  
  
4. Program.cs 'i açın. Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. `Main` Yönteminin içeriğini, tek <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> bir etkinlik içeren ve yeni bir dinamik etkinliğin <xref:System.Activities.DynamicActivity.Implementation%2A> özelliğine atayan bir etkinlik oluşturan aşağıdaki kodla değiştirin.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. Uygulamayı yürütün. "Merhaba Dünya!" metnini içeren bir konsol penceresi görüntülenmektedir.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>XAML kullanarak çalışma zamanında etkinlik oluşturmak için  
  
1. Visual Studio 2010 ' i açın.  
  
2. **Dosya**, **Yeni**, **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#**  altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **Iş akışı konsol uygulaması** ' nı seçin. Yeni projeyi DynamicActivitySample olarak adlandırın.  
  
3. Merhaba etkinlik projesinde Workflow1. xaml ' i açın. Tasarımcının alt kısmındaki **bağımsız değişkenler** seçeneğine tıklayın. Türünde `In` `TextToWrite` adlı Yenibirbağımsızdeğişkenoluşturun.`String`  
  
4. Araç kutusunun **temel öğeler** bölümünden bir **WriteLine** etkinliğini tasarımcı yüzeyine sürükleyin. Etkinliğin Text özelliğine `TextToWrite` değeri atayın .  
  
5. Program.cs 'i açın. Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. `Main` Yönteminin içeriğini aşağıdaki kodla değiştirin.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Uygulamayı yürütün. "Merhaba Dünya!" metnini içeren bir konsol penceresi görüneceği.  
  
8. **Çözüm Gezgini** Workflow1. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin. Etkinlik sınıfının ile `x:Class` oluşturulduğunu ve özelliğinin ile `x:Property`oluşturulduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md)
