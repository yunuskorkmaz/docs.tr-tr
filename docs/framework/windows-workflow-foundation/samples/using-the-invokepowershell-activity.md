---
title: Invokepowershell etkinliğini kullanma
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560980"
---
# <a name="using-the-invokepowershell-activity"></a>Invokepowershell etkinliğini kullanma
Invokepowershell örnek Windows PowerShell komutlarını kullanarak çağırmak nasıl gösterir `InvokePowerShell` etkinlik.  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Windows PowerShell komutlarının basit yenilik.  
  
-   Windows PowerShell çıkış hattından değerleri almak ve iş akışı değişkenleri depolayabilirsiniz.  
  
-   Verileri, windows PowerShell ile bir yürütme komutu için giriş potansiyel olarak geçirir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, aşağıdaki üç projeleri içerir.  
  
|Proje adı|Açıklama|Ana dosyaları|  
|------------------|-----------------|----------------|  
|CodedClient|PowerShell etkinliğini kullanan örnek istemci uygulaması.|-   **Program.cs**: program aracılığıyla Invokepowershell etkinliğini çağıran bir dizisi tabanlı bir iş akışı oluşturur.|  
|DesignerClient|Bir dizi içeren özel etkinlikler `InvokePowerShell` özel etkinlik ve diğer çeşitli özel etkinlikler ve bunları kullanan bir iş akışı.|<ul><li>Etkinlikleri:<br /><br /> <ul><li>**PrintCollection.cs**: konsola bir koleksiyondaki tüm öğeleri yazdıran Yardımcısı etkinlik.</li><li>**ReadLine.cs**: konsoldan okuma giriş için bir yardımcı etkinlik.</li></ul></li><li>Dosya sistemi:<br /><br /> <ul><li>**Copy.XAML**: bir dosyayı kopyalar bir etkinlik.</li><li>**CreateFile.xaml**: aktivite bir dosya oluşturur.</li><li>**DeleteFile.xaml**: bir dosyayı silen bir etkinlik.</li><li>**MakeDir.xaml**: bir dizin oluşturan bir etkinlik.</li><li>**Move.XAML**: bir dosyayı taşır bir etkinlik.</li><li>**ReadFile.xaml**: bir dosyayı okur ve içeriği döndüren bir etkinlik.</li><li>**TestPath.xaml**: yol varlığını test eden bir etkinlik.</li></ul></li><li>İşlem:<br /><br /> <ul><li>**GetProcess.xaml**: aktivite çalışan işlemlerin bir listesi alır.</li><li>**StopProcess.xaml**: belirli bir işlem durduran bir etkinlik.</li></ul></li><li>**Program.cs**: Sıra1 iş akışını çağırır.</li><li>**Sequence1.XAML**: sırası tabanlı bir iş akışı.</li></ul>|  
|PowerShell|`InvokePowerShell` Etkinlik ve onun ilişkili tasarımcıları.|Etkinlik dosyaları<br /><br /> -   **ExecutePowerShell.cs**: etkinliğinin ana yürütme mantığı.<br />-   **InvokePowerShell.cs**: Genel (dönüş değeri) sürümü ve genel olmayan (dönüş değeri) sürümü içeren ana yürütme mantığı çevresinde bir sarmalayıcı. Bu etkinlik için ortak arabirimdir.<br />-   **NoPersistZone.cs**: Bu etkinlik herhangi bir alt etkinlik kalıcı engeller. Bu sınıf içinde kullanılan `InvokePowerShell` etkinliği engellemek için etkinlik uygulaması kalıcı Orta yürütme.<br /><br /> Tasarımcı dosyaları:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: bağımsız değişkenleri düzenlemek kullanıcıya izin veren bir Windows iletişim `InvokePowerShell` etkinlik.<br />2.  **GenericInvokePowerShellDesigner.xaml** ve **GenericInvokePowerShellDesigner.xaml.cs**: genel görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** ve **InvokePowerShellDesigner.cs**: genel olmayan görünümünü tanımlayan `InvokePowerShell` etkinliğinde [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 İstemci projeleri kullanımını anlaşıldıktan sonra PowerShell etkinlik iç işlevleri anlamak daha kolay olsa da ilk olarak ele alınmıştır.  
  
## <a name="using-this-sample"></a>Bu örnek kullanma  
 Aşağıdaki bölümlerde, üç projelerinin örnekte nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="using-the-coded-client-project"></a>Kodlanmış istemci projesi kullanma  
 Örnek istemci programlı olarak kullanmanın birkaç farklı yöntem örneklerini içeren bir sıralama etkinliği oluşturur `InvokePowerShell` etkinlik. Not defterini ilk çağrı başlatır.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 İkinci çağrı yerel makine üzerinde çalışan işlemlerin bir listesini alır.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` değişkeni komutunun çıktısını depolamak için kullanılır.  
  
 Sonraki çağrı, tek tek her PowerShell çağırma çıktıda bir sonradan işleme adımı çalıştırılacak gösterilmiştir. `InitializationAction` Her işlem için dize gösterimini çıkarır işlevi ayarlanır. Bu dizeler koleksiyonu döndürülür `Output` değişkenini `InvokePowerShell<string>` etkinlik.  
  
 Başarılı `InvokePowerShell` çağrılarını göstermek veri geçirme etkinliği ve çıktıları ve hataları alınıyor.  
  
### <a name="using-the-designer-client-project"></a>Tasarımcı istemci projesi kullanma  
 Özel etkinlikler, neredeyse her biri yerleşik içeren bir dizi DesignerClient proje oluşur `InvokePowerShell` etkinlik. Çoğu etkinliklerinin genel olmayan sürümü, çağrı `InvokePowerShell` etkinliği ve bir dönüş değeri beklemiyoruz. Diğer etkinlikler genel kullanmanız `InvokePowerShell` etkinliği ve kullanım `InitializationAction` sonuçları sonrası işlemek için bağımsız değişken.  
  
## <a name="using-the-powershell-project"></a>PowerShell projesine kullanma  
 Ana eylem etkinlik gerçekleştikten `ExecutePowerShell` sınıfı. PowerShell komutların yürütülmesini temel iş akışı iş parçacığı engellemelisiniz değil çünkü etkinlik devralarak zaman uyumsuz bir etkinlik olması oluşturulur <xref:System.Activities.AsyncCodeActivity> sınıfı.  
  
 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Yöntemi etkinlik çalıştırmaya başlamak için iş akışı çalışma zamanı tarafından çağrılır. PowerShell işlem hattını oluşturmak için PowerShell API'lerini çağırarak başlar.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 Bir PowerShell komut oluşturur ve parametreler ve değişkenler ile doldurur.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 İçinde yöneltilen girişleri de bu noktada işlem hattının gönderilir. Son olarak, işlem hattı içinde sarmalanmış bir `PipelineInvokerAsyncResult` nesne ve döndürülür. `PipelineInvokerAsyncResult` Nesne dinleyicisi kaydeder ve işlem hattı çağırır.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Yürütme sona erdiğinde çıktısının ve hataların aynı içinde depolanan `PipelineInvokerAsyncResult` nesne ve denetim devredildiği geri akışı çalışma zamanı için ilk olarak geçirilen geri çağırma yöntemi çağırarak <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 Yöntemin yürütülmesine sonunda, iş akışı çalışma zamanı etkinliğin çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi.  
  
 `InvokePowerShell` Sınıfı sarar `ExecutePowerShellCommand` sınıfı ve etkinliği; genel bir sürümü iki sürümü ve genel olmayan sürümü oluşturur. Genel tür için tek tek sonuçları genel sürüm dönüştüren ise genel olmayan sürüm PowerShell yürütme çıkışını doğrudan döndürür.  
  
 Etkinliğin genel sürüm çağıran bir sıralı iş akışı uygulanan `ExecutePowerShellCommand` ve sonuçları sonrası işler. Sonuç koleksiyondaki her öğe için işlem sonrası adımı çağırır `InitializationAction` ayarlanmış ise. Aksi takdirde, basit bir tür dönüştürme yapar.  
  
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
  
 Her iki `InvokePowerShell` etkinlikleri (genel ve genel olmayan), bir tasarımcı oluşturuldu. InvokePowerShellDesigner.xaml ve ilişkili .cs dosyası görünümünü tanımlamak [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] genel olmayan sürümünün `InvokePowerShell` etkinlik. InvokePowerShellDesigner.xaml içinde bir <xref:System.Windows.Controls.DockPanel> grafik arabirimini temsil etmek için kullanılır.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Unutmayın `Text` özelliktir metin kutusunun etkinliğin değerini sağlar, iki yönlü bir bağlama `CommandText` özelliği, Tasarımcı değeri giriş eşdeğerdir.  
  
 GenericInvokePowerShellDesigner.xaml ve ilişkili .cs dosyası tanımlamak için genel grafik arabirim `InvokePowerShell` etkinlik. Ayarlanacak kullanıcılar izin verdiğinden Tasarımcı biraz daha karmaşık bir `InitializationAction`. Kullanımını anahtar öğedir <xref:System.Activities.Presentation.WorkflowItemPresenter> Sürükle izin vermek için ve bırakma bağımlı etkinliklerin `InvokePowerShell` Tasarımcı yüzeyine bırakın.  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 Tasarımcı özelleştirme tasarım tuvalde etkinlik görünümünü tanımlayan .xaml dosyalarını durdurmaz. Etkinlik parametreleri görüntülemek için kullanılan iletişim kutuları da özelleştirilebilir. Bu parametreler ve PowerShell değişkenleri PowerShell komutlarını davranışını etkiler. Etkinlik olarak sunan <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` türleri. Bu tür düzenlemenize olanak sağlayacak iletişim kutusu ArgumentDictionaryEditor.cs ve PropertyEditorResources.xaml PropertyEditorResources.cs tanımlayın.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
 Bu örneği çalıştırmak için Windows PowerShell yüklemeniz gerekir. Windows PowerShell Bu konumdan yüklenebilir: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Kodlanmış istemciyi çalıştırmak için  
  
1.  Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüme sağ tıklayın ve derleyin.  
  
3.  Sağ **CodedClient** seçin ve proje **başlangıç projesi olarak ayarla**.  
  
4.  Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
#### <a name="to-run-the-designer-client"></a>Tasarımcı istemciyi çalıştırmak için  
  
1.  Açık PowerShell.sln kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüme sağ tıklayın ve derleyin.  
  
3.  Sağ **DesignerClient** seçin ve proje **başlangıç projesi olarak ayarla**.  
  
4.  Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="known-issues"></a>Bilinen Sorunlar  
  
1.  Başvuru değilse `InvokePowerShell` etkinlik derlemesini veya bir yapı hatası başka bir proje sonuçlarında projeden, el ile eklemeniz gerekebilir `<SpecificVersion>True</SpecificVersion>` başvurduğu satırı altında yeni projenin .csproj dosyasını bir öğeye `InvokePowerShell`.  
  
2.  Windows PowerShell yüklü değilse, eklediğiniz hemen sonra aşağıdaki hata iletisini Visual Studio'da görüntülenir bir `InvokePowerShell` üzerine bir iş akışı etkinlik: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  Windows PowerShell 2.0 sürümünde, program aracılığıyla arama `$input.MoveNext()` başarısız olur ve betikleri kullanarak `$input.MoveNext()` istenmeyen hatalara ve sonuçlar üretir. Bu sorunu geçici olarak çözmek için PowerShell fiili kullanmayı düşünün `foreach` çağırmak yerine `MoveNext()` bir dizi yineleme olduğunda.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`