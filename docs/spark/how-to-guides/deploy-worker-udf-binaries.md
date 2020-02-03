---
title: Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtma
description: Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtmayı öğrenin.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f9197ca3cf8066f0849ebbe70d7757c9035d02f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748533"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtma

Bu nasıl yapılır, Apache Spark çalışan ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtımı hakkında genel yönergeler sağlar. Ayarlanacak ortam değişkenlerini ve `spark-submit`uygulamaları başlatmak için yaygın olarak kullanılan bazı parametreleri öğrenirsiniz.

## <a name="configurations"></a>Yapılandırmalar
Yapılandırmalarda, Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtmak üzere genel ortam değişkenlerini ve parametre ayarlarını gösterir.

### <a name="environment-variables"></a>Ortam değişkenleri
Çalışanları dağıttığınızda ve UDF 'Leri yazarken, ayarlamanız gerekebilecek yaygın olarak kullanılan birkaç ortam değişkeni vardır: 

| Ortam değişkeni         | Açıklama
| :--------------------------- | :---------- 
| DOTNET_WORKER_DIR            | <code>Microsoft.Spark.Worker</code> ikilisinin oluşturulduğu yol.</br>Spark sürücüsü tarafından kullanılır ve Spark yürüticilerine geçirilir. Bu değişken ayarlanmamışsa, Spark yürüticileri <code>PATH</code> ortam değişkeninde belirtilen yolda arama yapılır.</br>_ör. "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | <code>Microsoft.Spark.Worker</code> derlemeleri yükleyecek olan virgülle ayrılmış yollar.</br>Bir yol "." ile başlıyorsa, çalışma dizini 'nin önüne getirilir. **Yarn modunda**, "." kapsayıcının çalışma dizinini temsil eder.</br>_ör. "C:\Users\\&lt;Kullanıcı adı&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;DotNet sürüm&gt;"_
| DOTNET_WORKER_DEBUG          | <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF hata ayıklaması</a>yapmak istiyorsanız, <code>spark-submit</code>çalıştırmadan önce bu ortam değişkenini <code>1</code> olarak ayarlayın.

### <a name="parameter-options"></a>Parametre seçenekleri
Spark uygulaması [gruplandırıldıktan](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)sonra, `spark-submit`kullanarak başlatabilirsiniz. Aşağıdaki tabloda, yaygın olarak kullanılan seçeneklerden bazıları gösterilmektedir: 

| Parametre Adı        | Açıklama
| :---------------------| :---------- 
| --sınıfı               | Uygulamanız için giriş noktası.</br>_Örneğin, org. Apache. spark. deploy. DotNet. DotnetRunner_
| --Master              | Kümenin <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">ana URL 'si</a> .</br>_ör. yarn_
| --Deploy-Mode         | Sürücünüzü çalışan düğümlerinde (<code>cluster</code>) veya yerel olarak dış istemci olarak (<code>client</code>) dağıtıp dağıtmeyeceğinizi belirtir.</br>Varsayılan: <code>client</code>
| --conf                | <code>key=value</code> biçiminde rastgele Spark yapılandırma özelliği.</br>_ör. spark. yarn. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --dosyalar               | Her bir yürütücü çalışma dizinine yerleştirilecek dosyaların virgülle ayrılmış listesi.<br/><ul><li>Bu seçeneğin yalnızca Yarn modu için geçerli olduğunu lütfen unutmayın.</li><li>Hadoop için # benzer bir dosya adı belirtmeyi destekler.</br></ul>_ör. <code>myLocalSparkApp.dll#appSeen.dll</code>. Uygulamanızın YARN 'de çalışırken <code>myLocalSparkApp.dll</code> başvurmak için <code>appSeen.dll</code> adını kullanması gerekir._</li>
| --Arşivler          | Her bir yürütücünün çalışma dizininde Ayıklanacak arşivlerin virgülle ayrılmış listesi.</br><ul><li>Bu seçeneğin yalnızca Yarn modu için geçerli olduğunu lütfen unutmayın.</li><li>Hadoop için # benzer bir dosya adı belirtmeyi destekler.</br></ul>_ör. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. Bu, ZIP dosyasını kopyalayıp <code>worker</code> klasöre ayıklar._</li>
| Uygulama-jar       | Uygulamanız ve tüm bağımlılıklar dahil olmak üzere bir paketlenmiş jar yolu.</br>_Örneğin, hdfs://&lt;jar&gt;/Microsoft-parlak-&lt;sürümü&gt;. jar_
| uygulama-bağımsız değişkenler | Varsa, ana sınıfınızın ana yöntemine geçirilen bağımsız değişkenler.</br>_Örneğin, uygulamanızın&gt;&lt;&lt;/uygulamanızın adı&gt;uygulama adı &lt;&gt; App args &lt;_ &gt;

> [!NOTE]
> Uygulamaları `spark-submit`başlatırken `application-jar` önce tüm `--options` belirtin, aksi takdirde yok sayılır. Daha fazla bilgi için bkz. [`spark-submit` seçenekler](https://spark.apache.org/docs/latest/submitting-applications.html) ve [Yarn ayrıntıları üzerinde Spark çalıştırma](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Bir Spark uygulamasını UDF 'ler ile çalıştırdığımda bir ' FileNotFoundException ' hatası alıyorum. Ne yapmalıyım?
> **Hata:** [hata] [TaskRunner] [0] processstream () özel durumla başarısız oldu: System. IO. FileNotFoundException: bütünleştirilmiş kod ' MySparkApp, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = null ' dosya bulunamadı: ' mySparkApp. dll '

**Cevap:** `DOTNET_ASSEMBLY_SEARCH_PATHS` ortamı değişkeninin doğru şekilde ayarlandığından emin olun. `mySparkApp.dll`içeren yol olmalıdır.

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Apache Spark sürümünü .NET 'mi yükselttikten sonra `DOTNET_WORKER_DIR` ortam değişkenini sıfırladıktan sonra neden hala şu `IOException` hatasını alıyorum?
> **Hata:** 0,0 (TID 24, localhost, yürütücü sürücüsü) 11,0 aşamasında görevi kayboldu: Java. IO. IOException: "Microsoft. spark. Worker. exe" programı çalıştırılamıyor: CreateProcess hatası = 2, sistem belirtilen dosyayı bulamıyor.

**Cevap:** En son ortam değişkeni değerlerini alabilmeniz için önce PowerShell pencerenizi (veya diğer komut pencerelerini) yeniden başlatmayı deneyin. Ardından programınızı başlatın.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Spark uygulamamı gönderdikten sonra, `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`hata alıyorum.
> **Hata:** [hata] [TaskRunner] [0] processstream (), şu özel durumla başarısız oldu: System. TypeLoadException: ' mscorlib, Version = 4.0.0.0, Culture = neutral, PublicKeyToken =... ' derlemesinden ' System. Runtime. Remoting. bağlamadı ' türü yüklenemedi.

**Cevap:** Kullandığınız `Microsoft.Spark.Worker` sürümünü denetleyin. İki sürüm vardır: **.NET Framework 4.6.1** ve **.NET Core 2.1. x**. Bu durumda, `System.Runtime.Remoting.Contexts.Context` yalnızca .NET Framework olduğundan `Microsoft.Spark.Worker.net461.win-x64-<version>` ( [indirebileceğiniz](https://github.com/dotnet/spark/releases)) kullanılmalıdır.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Nasıl yaparım? Spark uygulamamı YARN 'de UDF 'ler ile Çalıştır? Hangi ortam değişkenlerini ve parametreleri kullanmalıyım?

**Cevap:** YARN 'de Spark uygulamasını başlatmak için, ortam değişkenlerinin `spark.yarn.appMasterEnv.[EnvironmentVariableName]`olarak belirtilmesi gerekir. Lütfen `spark-submit`kullanarak aşağıda örnek olarak bakın:

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama](../how-to-guides/debug.md)
