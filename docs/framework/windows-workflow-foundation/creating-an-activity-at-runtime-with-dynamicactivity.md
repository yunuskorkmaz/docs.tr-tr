---
title: Bir etkinlik, Dynamicactivity'nin ile çalışma zamanında oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774081"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Bir etkinlik, Dynamicactivity'nin ile çalışma zamanında oluşturma
<xref:System.Activities.DynamicActivity> bir somut, korumalı bir public Oluşturucu ile sınıftır. <xref:System.Activities.DynamicActivity> bir etkinlik yerli kullanarak çalışma zamanında etkinlik işlevselliğini bir araya getirmek için kullanılabilir  
  
## <a name="dynamicactivity-features"></a>DynamicActivity özellikleri  
 <xref:System.Activities.DynamicActivity> yürütme özellikleri ve bağımsız değişkenler için erişim, ancak hiçbir alt etkinlikler zamanlamak veya izleme gibi çalışma zamanı hizmetlerine erişim vardır.  
  
 İş akışı kullanarak üst düzey özellikleri ayarlanabilir <xref:System.Activities.Argument> nesneleri. Kesinlik temelli kod içinde bu bağımsız değişkenler CLR özellikleri yeni bir türü kullanılarak oluşturulur. XAML içinde kullanılarak bildirilirler `x:Class` ve `x:Member` etiketler.  
  
 Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.DynamicActivity> Tasarımcısı kullanarak arabirimi <xref:System.ComponentModel.ICustomTypeDescriptor>. Tasarımcısı'nda oluşturulan etkinlikleri kullanarak dinamik olarak yüklenebilir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, aşağıdaki yordamda gösterildiği gibi.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Kesin kod kullanarak çalışma zamanında bir etkinlik oluşturmak için  
  
1. OpenVisual Studio 2010.  
  
2. Seçin **dosya**, **yeni**, **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **sıralı iş akışı konsol uygulaması** içinde **şablonları** penceresi. Yeni Proje DynamicActivitySample adı.  
  
3. Workflow1.XAML HelloActivity projeye sağ tıklayıp **Sil**.  
  
4. Program.cs dosyasını açın. Aşağıdaki yönerge dosyasının en üstüne ekleyin.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5. Öğesinin içeriğini değiştirin `Main` yöntemini aşağıdaki kodla oluşturan bir <xref:System.Activities.Statements.Sequence> içeren tek bir etkinlik <xref:System.Activities.Statements.WriteLine> etkinlik ve atar <xref:System.Activities.DynamicActivity.Implementation%2A> yeni dinamik bir etkinliğin özelliği.  
  
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
  
6. Uygulamayı çalıştırın. "Hello World!" metni ile bir konsol penceresi görüntüler.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>XAML kullanarak çalışma zamanında bir etkinlik oluşturmak için  
  
1. Visual Studio 2010'u açın.  
  
2. Seçin **dosya**, **yeni**, **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **iş akışı konsol uygulaması** içinde **şablonları** penceresi. Yeni Proje DynamicActivitySample adı.  
  
3. Workflow1.XAML HelloActivity projeyi açın. Tıklayın **bağımsız değişkenleri** Tasarımcısı'nın altındaki seçeneği. Yeni bir `In` bağımsız değişken olarak adlandırılan `TextToWrite` türü `String`.  
  
4. Sürükleme bir **WriteLine** etkinliğinden **Temelleri** Tasarımcı yüzeyine araç bölümü. Değer atamak `TextToWrite` için **metin** etkinliğin özelliği.  
  
5. Program.cs dosyasını açın. Aşağıdaki yönerge dosyasının en üstüne ekleyin.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Öğesinin içeriğini değiştirin `Main` yöntemini aşağıdaki kod ile.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Uygulamayı çalıştırın. "Hello World!" metni ile bir konsol penceresi görünür.  
  
8. Workflow1.xaml dosyaya sağ **Çözüm Gezgini** seçip **kodu görüntüle**. Etkinliği sınıf oluşturulur Not `x:Class` ve özelliği ile oluşturulan `x:Property`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md)
