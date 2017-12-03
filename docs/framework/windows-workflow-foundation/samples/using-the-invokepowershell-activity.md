---
title: "InvokePowerShell etkinliğini kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3ef8b539e490911e5454fe87db483508cc8a5d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokepowershell-activity"></a>InvokePowerShell etkinliğini kullanma
InvokePowerShell örnek Windows PowerShell komutlarını kullanarak çağrılacak gösterilmiştir `InvokePowerShell` etkinlik.  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Windows PowerShell komutlarının basit yenilik.  
  
-   Windows PowerShell çıkış ardışık düzen değerleri almak ve iş akışı değişkenleri depolayabilirsiniz.  
  
-   Verileri windows PowerShell yürütme komut için giriş potansiyel olarak geçirir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, aşağıdaki üç projeleri içerir.  
  
|Proje adı|Açıklama|Ana dosyaları|  
|------------------|-----------------|----------------|  
|CodedClient|PowerShell etkinliği kullanan bir örnek istemci uygulaması.|-   **Program.cs**: program aracılığıyla InvokePowerShell etkinlik çağıran bir sıra tabanlı bir iş akışı oluşturur.|  
|DesignerClient|İçeren özel etkinlikler kümesi `InvokePowerShell` özel etkinlik ve çeşitli diğer özel etkinlikler ve bunları kullanan bir iş akışı.|<ul><li>Etkinlikleri:<br /><br /> <ul><li>**PrintCollection.cs**: konsoluna bir koleksiyondaki tüm öğeleri yazdırır Yardımcısı etkinlik.</li><li>**ReadLine.cs**: konsoldan okuma girişi için bir yardımcı etkinlik.</li></ul></li><li>Dosya sistemi:<br /><br /> <ul><li>**Copy.XAML**: bir dosya kopyalayan bir etkinlik.</li><li>**CreateFile.xaml**: aktivite bir dosya oluşturur.</li><li>**DeleteFile.xaml**: bir dosyayı siler bir etkinlik.</li><li>**MakeDir.xaml**: bir dizin oluşturan bir etkinlik.</li><li>**Move.XAML**: bir dosyayı taşır bir etkinlik.</li><li>**ReadFile.xaml**: bir dosyayı okur ve içeriği döndüren bir etkinlik.</li><li>**TestPath.xaml**: bir yol varlığını testleri bir etkinlik.</li></ul></li><li>İşlem:<br /><br /> <ul><li>**GetProcess.xaml**: aktivite çalışan işlemlerin listesini alır.</li><li>**StopProcess.xaml**: belirli bir işlemi durdurur bir etkinlik.</li></ul></li><li>**Program.cs**: Sıra1 iş akışını çağırır.</li><li>**Sequence1.XAML**: dizisi tabanlı bir iş akışı.</li></ul>|  
|PowerShell|`InvokePowerShell` Etkinliği ve onun ilişkili tasarımcıları.|Etkinlik dosyaları<br /><br /> -   **ExecutePowerShell.cs**: ana yürütme mantığını etkinliği.<br />-   **InvokePowerShell.cs**: bir genel (dönüş değeri) sürümü ve genel olmayan (dönüş değeri) sürümü içeren ana yürütme mantığı çevresinde sarmalayıcı. Bu etkinlik için ortak arabirimdir.<br />-   **NoPersistZone.cs**: kalıcı gelen tüm alt etkinlikler bu etkinliği engeller. Bu sınıf içinde kullanılan `InvokePowerShell` etkinlik engellemek için etkinlik uygulama kalıcı Orta yürütme.<br /><br /> Tasarımcı dosyalar:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: bağımsız değişkenleri düzenlemesine olanak tanır bir Windows iletişim `InvokePowerShell` etkinlik.<br />2.  **GenericInvokePowerShellDesigner.xaml** ve **GenericInvokePowerShellDesigner.xaml.cs**: genel görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** ve **InvokePowerShellDesigner.cs**: genel olmayan görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Kullanımı anladım sonra PowerShell etkinlik iç işlevleri anlamak daha kolay olduğundan istemci projeleri ilk olarak ele alınmıştır.  
  
## <a name="using-this-sample"></a>Bu örnek kullanma  
 Aşağıdaki bölümlerde üç projelerinin örnekte nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="using-the-coded-client-project"></a>Kodlanmış istemci projesi kullanma  
 Örnek istemci programlı olarak kullanmanın birkaç farklı yöntem örnekleri içeren bir sıralı etkinlik oluşturur `InvokePowerShell` etkinlik. İlk çağırma Notepad başlatır.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 İkinci çağırma yerel makine üzerinde çalışan işlemlerin bir listesini alır.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output`değişkeni komutunun çıktısını depolamak için kullanılır.  
  
 Sonraki çağrı, bir işlem sonrası adımı PowerShell çağırma tek tek her çıkışta çalıştırmak gösterilmiştir. `InitializationAction`Her işlem için dize gösterimi çıkarır işlevi ayarlanır. Bu dizeler koleksiyonu döndürülür `Output` tarafından değişken `InvokePowerShell<string>` etkinlik.  
  
 Başarılı `InvokePowerShell` çağrıları etkinlik ve çıkış ve hataları alma veri geçirme göstermektedir.  
  
### <a name="using-the-designer-client-project"></a>Tasarımcı istemci projesi kullanma  
 Özel etkinlikler, neredeyse her biri yerleşik içeren bir dizi DesignerClient proje oluşur `InvokePowerShell` etkinlik. Etkinliklerin çoğu çağrı genel olmayan sürümü `InvokePowerShell` etkinliği ve bir dönüş değeri beklemediğiniz. Diğer etkinlikler genel sürümünü kullanmanız `InvokePowerShell` etkinlik ve kullanım `InitializationAction` sonuçları sonrası işlemek için bağımsız değişken.  
  
## <a name="using-the-powershell-project"></a>PowerShell projesine kullanma  
 Ana eylem etkinliğin gerçekleşir `ExecutePowerShell` sınıfı. PowerShell komutlarının yürütülmesini ana iş akışı iş parçacığı uğramaması değil çünkü etkinlik devralarak zaman uyumsuz bir etkinlik olarak oluşturulan <xref:System.Activities.AsyncCodeActivity> sınıfı.  
  
 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Yöntemi, etkinlik çalıştırmaya başlamak için iş akışı çalışma zamanı tarafından çağrılır. PowerShell komut zinciri oluşturmak için PowerShell API'ları çağırarak başlar.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 PowerShell komut oluşturur ve parametreler ve değişkenler ile doldurur.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 İçinde yöneltilen girişleri de bu noktada ardışık düzene gönderilir. Ardışık Düzen son olarak, paketlenir bir `PipelineInvokerAsyncResult` nesne ve döndürülür. `PipelineInvokerAsyncResult` Nesne dinleyicisi kaydeder ve ardışık düzen çağırır.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Yürütme tamamlandığında, çıkış ve hata aynı içinde depolanan `PipelineInvokerAsyncResult` nesne ve denetim karmalayan geri için iş akışı çalışma zamanı için başlangıçta kendisine geçirilen geri çağırma yöntemini çağırarak <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 Yöntemin yürütme sonunda, iş akışı çalışma zamanı etkinliğin çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi.  
  
 `InvokePowerShell` Sınıf sarmalayan `ExecutePowerShellCommand` sınıf ve etkinlik; genel bir sürümü iki sürümü ve genel olmayan sürümünü oluşturur. Genel tür bağımsız sonuçları genel sürüm dönüştürür ancak genel olmayan sürümü PowerShell yürütme çıktısı, doğrudan döndürür.  
  
 Etkinlik genel sürümünü çağıran sıralı iş akışı olarak uygulanan `ExecutePowerShellCommand` ve sonuçlarını sonrası işler. Sonuç koleksiyondaki her öğe için işlem sonrası adımı çağırır `InitializationAction` Bu ayarlanırsa. Aksi takdirde, basit bir cast yapar.  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 Her iki `InvokePowerShell` etkinlikleri (genel ve genel olmayan), bir tasarımcı oluşturuldu. InvokePowerShellDesigner.xaml ve onun ilişkili .cs dosyası tanımlayın görünümünü [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] genel olmayan sürümü için `InvokePowerShell` etkinlik. InvokePowerShellDesigner.xaml içinde bir <xref:System.Windows.Controls.DockPanel> grafik arabirim temsil etmek için kullanılır.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Unutmayın `Text` özelliktir metin kutusunun etkinliğin değerini sağlar iki yönlü bir bağlama `CommandText` özelliği, Tasarımcı değeri giriş eşdeğerdir.  
  
 GenericInvokePowerShellDesigner.xaml ve onun ilişkili .cs dosyası tanımlayın genel için grafik arabirimine `InvokePowerShell` etkinlik. Ayarlamak kullanıcılara izin verdiği için tasarımcı biraz daha karmaşıktır bir `InitializationAction`. Kullanımını anahtar öğedir <xref:System.Activities.Presentation.WorkflowItemPresenter> sürükleme izin vermek ve bırakma alt etkinliklerin `InvokePowerShell` Tasarımcı yüzeyine.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 Tasarımcı özelleştirme tasarım tuvalde etkinlik görünümünü tanımlamak .xaml dosyalarla durdurmaz. Etkinlik parametreleri görüntülemek için kullanılan iletişim kutuları da özelleştirilebilir. Bu parametreler ve PowerShell değişkenleri PowerShell komutlarını davranışını etkiler. Etkinlik olarak kullanıma sunar <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` türleri. Bu tür düzenlemenizi sağlar iletişim kutusu ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml ve PropertyEditorResources.cs tanımlayın.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
 Bu örneği çalıştırmak için Windows PowerShell yüklemeniz gerekir. Windows PowerShell Bu konumdan yüklenebilir: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Kodlanmış istemci çalıştırmak için  
  
1.  Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüme sağ tıklayın ve bunu oluşturun.  
  
3.  Sağ **CodedClient** proje ve seçin **başlangıç projesi olarak ayarla**.  
  
4.  Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
#### <a name="to-run-the-designer-client"></a>Tasarımcı istemci çalıştırmak için  
  
1.  Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüme sağ tıklayın ve bunu oluşturun.  
  
3.  Sağ **DesignerClient** proje ve seçin **başlangıç projesi olarak ayarla**.  
  
4.  Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
## <a name="known-issues"></a>Bilinen Sorunlar  
  
1.  Başvuran varsa `InvokePowerShell` etkinlik derleme veya proje derleme hatası sonuçlarında başka bir projeden, ihtiyacınız olabilecek el ile eklemek `<SpecificVersion>True</SpecificVersion>` .csproj dosyasına başvuruda bulunan satırı altında yeni proje öğesi `InvokePowerShell`.  
  
2.  Windows PowerShell yüklü değil, eklediğiniz hemen Visual Studio aşağıdaki hata iletisi görüntülenir bir `InvokePowerShell` etkinliğini bir iş akışı üzerine:`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  Windows PowerShell 2. 0 ', program aracılığıyla arama `$input.MoveNext()` başarısız olur ve kullanan komut dosyaları `$input.MoveNext()` istenmeyen hataları ve sonuçlar üretir. Bu sorunu çözmek için PowerShell fiil kullanmayı düşünün `foreach` çağırmak yerine `MoveNext()` bir dizi dolaşırken.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`