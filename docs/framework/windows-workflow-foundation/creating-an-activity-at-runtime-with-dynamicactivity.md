---
title: Dinamik Aktivite ile Çalışma Zamanında Etkinlik Oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182986"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Dinamik Aktivite ile Çalışma Zamanında Etkinlik Oluşturma
<xref:System.Activities.DynamicActivity>bir kamu yapıcı ile somut, mühürlü bir sınıftır. <xref:System.Activities.DynamicActivity>bir etkinlik DOM kullanarak çalışma zamanında etkinlik işlevselliğini birleştirmek için kullanılabilir.  
  
## <a name="dynamicactivity-features"></a>Dinamik Aktivite Özellikleri  
 <xref:System.Activities.DynamicActivity>yürütme özelliklerine, bağımsız değişkenlere ve değişkenlere erişimi vardır, ancak alt etkinlikleri zamanlama veya izleme gibi çalışma zamanı hizmetlerine erişim yoktur.  
  
 Üst düzey özellikler iş akışı <xref:System.Activities.Argument> nesneleri kullanılarak ayarlanabilir. Zorunlu kodda, bu bağımsız değişkenler yeni bir türde CLR özellikleri kullanılarak oluşturulur. XAML'de, bunlar `x:Class` kullanılarak `x:Member` ve etiketlere bildirilir.  
  
 Kullanarak tasarımcı <xref:System.Activities.DynamicActivity> ile arayüz <xref:System.ComponentModel.ICustomTypeDescriptor>kullanılarak yapılan etkinlikler. Tasarımcıda oluşturulan <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>etkinlikler, aşağıdaki yordamda gösterildiği gibi dinamik olarak yüklenebilir.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Zorunlu kodu kullanarak çalışma zamanında etkinlik oluşturmak için  
  
1. Açık Görsel Stüdyo 2010.  
  
2. **Dosya**yı seçin , **Yeni**, **Proje**. **Proje Türleri** penceresinde **Visual C#** altında **İş Akışı 4.0'ı** seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **Sıralı İş Akışı Konsolu Uygulamasını** seçin. Yeni projeye DynamicActivitySample adını verin.  
  
3. HelloActivity projesinde İş Akışı1.xaml'a sağ tıklayın ve **Sil'i**seçin.  
  
4. Açık Program.cs. Aşağıdaki yönergeyi dosyanın üst bölümüne ekleyin.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Yöntemin `Main` içeriğini, tek <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> bir etkinlik içeren ve yeni bir dinamik etkinliğin <xref:System.Activities.DynamicActivity.Implementation%2A> özelliğine atayan bir etkinlik oluşturan aşağıdaki kodla değiştirin.  
  
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
  
6. Uygulamayı yürütün. "Merhaba Dünya!" metninin yer verdiği bir konsol penceresi Görüntü -ler.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>XAML kullanarak çalışma zamanında etkinlik oluşturmak için  
  
1. Açık Görsel Studio 2010.  
  
2. **Dosya**yı seçin , **Yeni**, **Proje**. **Proje Türleri** penceresinde **Visual C#** altında **İş Akışı 4.0'ı** seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **İş Akışı Konsolu Uygulamasını** seçin. Yeni projeye DynamicActivitySample adını verin.  
  
3. HelloActivity projesinde İş Akışı1.xaml'ı açın. Tasarımcının altındaki **Bağımsız Değişkenler** seçeneğini tıklatın. Türü `String`adlı `In` `TextToWrite` yeni bir bağımsız değişken oluşturun.  
  
4. Bir **WriteLine** etkinliğini araç kutusunun **Primitives** bölümünden tasarımcı yüzeyine sürükleyin. Etkinliğin Metin `TextToWrite` özelliğine **Text** değeri atayın.  
  
5. Açık Program.cs. Aşağıdaki yönergeyi dosyanın üst bölümüne ekleyin.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. `Main` yönteminin içeriğini aşağıdaki kodla değiştirin.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Uygulamayı yürütün. "Merhaba Dünya!" metninin yer verdiği bir konsol penceresi Görünür.  
  
8. **Çözüm** Gezgini'ndeki Workflow1.xaml dosyasına sağ tıklayın ve **Kodu Görüntüle'yi**seçin. Etkinlik sınıfı ile `x:Class` oluşturulduğunu ve özelliğin `x:Property`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md)
