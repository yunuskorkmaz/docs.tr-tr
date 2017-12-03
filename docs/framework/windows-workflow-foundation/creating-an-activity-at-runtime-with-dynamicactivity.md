---
title: "DynamicActivity ile çalışma zamanında bir etkinlik oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d40fe3601cb8ad7c4f77cf50825da1deace5644e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>DynamicActivity ile çalışma zamanında bir etkinlik oluşturma
<xref:System.Activities.DynamicActivity>somut, korumalı bir public oluşturucuya sahip sınıfıdır. <xref:System.Activities.DynamicActivity>bir etkinlik DOM kullanarak çalışma zamanında etkinlik işlevleri bir araya getirmek için kullanılabilir  
  
## <a name="dynamicactivity-features"></a>DynamicActivity özellikleri  
 <xref:System.Activities.DynamicActivity>yürütme özellikleri, bağımsız değişkenleri ve değişkenleri erişimi, ancak alt etkinlikler zamanlama veya izleme gibi çalışma zamanı Hizmetleri erişimi vardır.  
  
 İş akışı kullanarak üst düzey özellikleri ayarlanabilir <xref:System.Activities.Argument> nesneleri. Kesinlik temelli kodda, bu bağımsız değişkenler, yeni bir tür CLR özellikleri kullanılarak oluşturulur. XAML'de, bunlar kullanılarak bildirilen `x:Class` ve `x:Member` etiketler.  
  
 Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.DynamicActivity> Tasarımcı kullanarak arabirimi <xref:System.ComponentModel.ICustomTypeDescriptor>. Tasarımcıda oluşturulan etkinlikleri kullanarak dinamik olarak yüklenebilir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, aşağıdaki yordamda gösterildiği gibi.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Kesinlik temelli kod kullanarak çalışma zamanında bir etkinlik oluşturmak için  
  
1.  Açık[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Seçin **dosya**, **yeni**, **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **sıralı iş akışı konsol uygulaması** içinde **şablonları** penceresi. Yeni Proje DynamicActivitySample olarak adlandırın.  
  
3.  Workflow1.XAML HelloActivity projeye sağ tıklayıp **silmek**.  
  
4.  Program.cs açın. Aşağıdaki yönergesi dosyasının üstüne ekleyin.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Değiştir `Main` oluşturur aşağıdaki kod ile yöntemi bir <xref:System.Activities.Statements.Sequence> içeren tek bir etkinlik <xref:System.Activities.Statements.WriteLine> etkinliği ve atar <xref:System.Activities.DynamicActivity.Implementation%2A> yeni bir dinamik etkinlik özelliği.  
  
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
  
6.  Uygulamayı çalıştırın. "Hello World!" metnini içeren bir konsol penceresi görüntüler.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>XAML kullanarak çalışma zamanında bir etkinlik oluşturmak için  
  
1.  Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Seçin **dosya**, **yeni**, **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **iş akışı konsol uygulaması** içinde **şablonları** penceresi. Yeni Proje DynamicActivitySample olarak adlandırın.  
  
3.  Workflow1.XAML HelloActivity projeyi açın. Tıklatın **bağımsız değişkenleri** Tasarımcısı'nın altındaki seçeneği. Yeni bir `In` bağımsız değişkeni olarak adlandırılan `TextToWrite` türü `String`.  
  
4.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** Tasarımcı yüzeyine araç bölümü. Değer atamak `TextToWrite` için **metin** etkinliğin özelliği.  
  
5.  Program.cs açın. Aşağıdaki yönergesi dosyasının üstüne ekleyin.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Değiştir `Main` aşağıdaki kod ile yöntemi.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Uygulamayı çalıştırın. "Hello World!" metnini içeren bir konsol penceresi görünür.  
  
8.  Workflow1.xaml dosyasında sağ **Çözüm Gezgini** seçip **görünümü kodu**. Etkinliği sınıf ile oluşturulan Not `x:Class` ve özelliği ile oluşturulan `x:Property`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş akışları, etkinlikler ve ifadeler kesinlik temelli kod kullanarak geliştirme](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [DynamicActivity oluşturma](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
