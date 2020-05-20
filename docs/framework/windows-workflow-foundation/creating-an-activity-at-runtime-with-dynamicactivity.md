---
title: DynamicActivity ile çalışma zamanında etkinlik oluşturma
description: DynamicActivity, ortak Oluşturucusu olan somut, mühürlenmiş bir sınıftır. Etkinlik DOM kullanarak çalışma zamanında etkinlik işlevselliğini birleştirmek için sınıfını kullanın.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421546"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>DynamicActivity ile çalışma zamanında etkinlik oluşturma
<xref:System.Activities.DynamicActivity>, ortak Oluşturucusu olan somut, mühürlenmiş bir sınıftır. <xref:System.Activities.DynamicActivity>Etkinlik DOM kullanılarak çalışma zamanında etkinlik işlevselliğini birleştirmek için kullanılabilir.  
  
## <a name="dynamicactivity-features"></a>DynamicActivity özellikleri  
 <xref:System.Activities.DynamicActivity>yürütme özelliklerine, bağımsız değişkenlere ve değişkenlere erişebilir, ancak alt etkinliklerin veya izlemenin zamanlanması gibi çalışma zamanı hizmetlerine erişemez.  
  
 En üst düzey özellikler, iş akışı nesneleri kullanılarak ayarlanabilir <xref:System.Activities.Argument> . Kesinlik temelli kodda, bu bağımsız değişkenler CLR özellikleri kullanılarak yeni bir tür üzerinde oluşturulur. XAML 'de, ve etiketleri kullanılarak bildirilmiştir `x:Class` `x:Member` .  
  
 <xref:System.Activities.DynamicActivity>Kullanılarak tasarımcı ile arabirim kullanılarak oluşturulan etkinlikler <xref:System.ComponentModel.ICustomTypeDescriptor> . Tasarımcıda oluşturulan etkinlikler <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> , aşağıdaki yordamda gösterildiği gibi kullanılarak dinamik olarak yüklenebilir.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Zorunlu kod kullanarak çalışma zamanında etkinlik oluşturmak için  
  
1. OpenVisual Studio 2010.  
  
2. **Dosya**, **Yeni**, **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **sıralı Iş akışı konsol uygulaması** ' nı seçin. Yeni projeyi DynamicActivitySample olarak adlandırın.  
  
3. Merhaba etkinlik projesinde Workflow1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.  
  
4. Program.cs 'i açın. Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Yönteminin içeriğini, `Main` <xref:System.Activities.Statements.Sequence> tek bir <xref:System.Activities.Statements.WriteLine> etkinlik içeren ve <xref:System.Activities.DynamicActivity.Implementation%2A> Yeni bir dinamik etkinliğin özelliğine atayan bir etkinlik oluşturan aşağıdaki kodla değiştirin.  
  
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
  
2. **Dosya**, **Yeni**, **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **Iş akışı konsol uygulaması** ' nı seçin. Yeni projeyi DynamicActivitySample olarak adlandırın.  
  
3. Merhaba etkinlik projesinde Workflow1. xaml ' i açın. Tasarımcının alt kısmındaki **bağımsız değişkenler** seçeneğine tıklayın. `In`Türünde adlı yeni bir bağımsız değişken oluşturun `TextToWrite` `String` .  
  
4. Araç kutusunun **temel öğeler** bölümünden bir **WriteLine** etkinliğini tasarımcı yüzeyine sürükleyin. `TextToWrite`Etkinliğin **Text** özelliğine değeri atayın.  
  
5. Program.cs 'i açın. Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. `Main` yönteminin içeriğini aşağıdaki kodla değiştirin.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Uygulamayı yürütün. "Merhaba Dünya!" metnini içeren bir konsol penceresi görüneceği.  
  
8. **Çözüm Gezgini** Workflow1. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin. Etkinlik sınıfının ile oluşturulduğunu `x:Class` ve özelliğinin ile oluşturulduğunu unutmayın `x:Property` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md)
