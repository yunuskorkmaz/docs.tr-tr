---
title: Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtma
description: Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtmayı öğrenin.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 042f336431a1c8cad7d94cf10cbe64b72ddfce5b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596467"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtma

Bu nasıl yapılır, Apache Spark çalışan ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtımı hakkında genel yönergeler sağlar. Ayarlanacak ortam değişkenlerinin yanı sıra uygulamaları ile başlatmak için yaygın olarak kullanılan bazı parametreleri öğrenirsiniz `spark-submit` .

## <a name="configurations"></a>Yapılandırmalar
Yapılandırmalarda, Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtmak üzere genel ortam değişkenlerini ve parametre ayarlarını gösterir.

### <a name="environment-variables"></a>Ortam değişkenleri
Çalışanları dağıttığınızda ve UDF 'Leri yazarken, ayarlamanız gerekebilecek yaygın olarak kullanılan birkaç ortam değişkeni vardır:

| Ortam değişkeni         | Açıklama
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | <code>Microsoft.Spark.Worker</code>İkilinin oluşturulduğu yol.</br>Spark sürücüsü tarafından kullanılır ve Spark yürüticilerine geçirilir. Bu değişken ayarlanmamışsa, Spark yürüticileri ortam değişkeninde belirtilen yolda arama yapılır <code>PATH</code> .</br>_ör. "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Derlemeleri yükleyecek olan virgülle ayrılmış yollar <code>Microsoft.Spark.Worker</code> .</br>Bir yol "." ile başlıyorsa, çalışma dizini 'nin önüne getirilir. **Yarn modunda**, "." kapsayıcının çalışma dizinini temsil eder.</br>_ör. "C:\Users \\ &lt; Kullanıcı adı &gt; \\ &lt; mysparkapp &gt; \Bin\Debug \\ &lt; DotNet sürümü &gt; "_
| DOTNET_WORKER_DEBUG          | <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF hata ayıklaması</a>yapmak istiyorsanız, bu ortam değişkenini <code>1</code> çalıştırılmadan önce olarak ayarlayın <code>spark-submit</code> .

### <a name="parameter-options"></a>Parametre seçenekleri
Spark uygulaması [paketlenmiş](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)olduktan sonra kullanarak başlatabilirsiniz `spark-submit` . Aşağıdaki tabloda, yaygın olarak kullanılan seçeneklerden bazıları gösterilmektedir:

| Parametre Adı        | Açıklama
| :---------------------| :----------
| --sınıfı               | Uygulamanız için giriş noktası.</br>_Örneğin, org. Apache. spark. deploy. DotNet. DotnetRunner_
| --Master              | Kümenin <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">ana URL 'si</a> .</br>_ör. yarn_
| --Deploy-Mode         | Sürücünüzü çalışan düğümlerinde ( <code>cluster</code> ) veya yerel olarak dış istemci olarak () dağıtıp dağıtmaktır <code>client</code> .</br>Varsayılanını<code>client</code>
| --conf                | Biçimde rastgele Spark yapılandırma özelliği <code>key=value</code> .</br>_ör. spark. yarn. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --dosyalar               | Her bir yürütücü çalışma dizinine yerleştirilecek dosyaların virgülle ayrılmış listesi.<br/><ul><li>Bu seçeneğin yalnızca Yarn modu için geçerli olduğunu lütfen unutmayın.</li><li>Hadoop için # benzer bir dosya adı belirtmeyi destekler.</br></ul>_ör. <code>myLocalSparkApp.dll#appSeen.dll</code> Uygulamanızın <code>appSeen.dll</code> YARN 'de çalışırken başvurmak için adı kullanması gerekir <code>myLocalSparkApp.dll</code> ._</li>
| --Arşivler          | Her bir yürütücünün çalışma dizininde Ayıklanacak arşivlerin virgülle ayrılmış listesi.</br><ul><li>Bu seçeneğin yalnızca Yarn modu için geçerli olduğunu lütfen unutmayın.</li><li>Hadoop için # benzer bir dosya adı belirtmeyi destekler.</br></ul>_ör. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> Bu, ZIP dosyasını kopyalayıp klasörüne çıkaracaktır <code>worker</code> ._</li>
| Uygulama-jar       | Uygulamanız ve tüm bağımlılıklar dahil olmak üzere bir paketlenmiş jar yolu.</br>_Örneğin, &lt; jar HDFS://yolu &gt; /Microsoft-parlak- &lt; Version &gt; . jar_
| uygulama-bağımsız değişkenler | Varsa, ana sınıfınızın ana yöntemine geçirilen bağımsız değişkenler.</br>_Örneğin App. zip uygulamanızın uygulamanızın adı HDFS://yolu, uygulama &lt; &gt; / &lt; &gt; &lt; &gt; &lt; bağımsız değişkenleri&gt;_

> [!NOTE]
> `--options` `application-jar` Uygulamaları ile başlatırken önce tüm `spark-submit` ' ı belirtin, aksi takdirde yok sayılır. Daha fazla bilgi için bkz. [ `spark-submit` Seçenekler](https://spark.apache.org/docs/latest/submitting-applications.html) ve bkz. [Yarn ayrıntıları üzerinde Spark](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Bir Spark uygulamasını UDF 'ler ile çalıştırdığımda bir ' FileNotFoundException ' hatası alıyorum. Ne yapmalıyım?
> **Hata:** [hata] [TaskRunner] [0] processstream () özel durumla başarısız oldu: System. IO. FileNotFoundException: bütünleştirilmiş kod ' MySparkApp, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = null ' dosya bulunamadı: ' mySparkApp. dll '

**Cevap:** `DOTNET_ASSEMBLY_SEARCH_PATHS`Ortam değişkeninin doğru şekilde ayarlandığından emin olun. Bunu içeren yol olmalıdır `mySparkApp.dll` .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>.NET My Apache Spark sürümü için yükselttikten ve ortam değişkenini sıfırladıktan sonra `DOTNET_WORKER_DIR` Neden yine de şu `IOException` hatayı alıyorum?
> **Hata:** 0,0 (TID 24, localhost, yürütücü sürücüsü) 11,0 aşamasında görevi kayboldu: Java. IO. IOException: "Microsoft. spark. Worker. exe" programı çalıştırılamıyor: CreateProcess hatası = 2, sistem belirtilen dosyayı bulamıyor.

**Cevap:** En son ortam değişkeni değerlerini alabilmeniz için önce PowerShell pencerenizi (veya diğer komut pencerelerini) yeniden başlatmayı deneyin. Ardından programınızı başlatın.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Spark uygulamamı gönderdikten sonra hata alıyorum `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'` .
> **Hata:** [hata] [TaskRunner] [0] processstream (), şu özel durumla başarısız oldu: System. TypeLoadException: ' mscorlib, Version = 4.0.0.0, Culture = neutral, PublicKeyToken =... ' derlemesinden ' System. Runtime. Remoting. bağlamadı ' türü yüklenemedi.

**Cevap:** Kullanmakta olduğunuz `Microsoft.Spark.Worker` sürümü denetleyin. İki sürüm vardır: **.NET Framework 4.6.1** ve **.NET Core 2.1. x**. Bu durumda, `Microsoft.Spark.Worker.net461.win-x64-<version>` ( [indirebileceğiniz](https://github.com/dotnet/spark/releases)) `System.Runtime.Remoting.Contexts.Context` yalnızca .NET Framework olduğundan kullanılmalıdır.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Nasıl yaparım? Spark uygulamamı YARN 'de UDF 'ler ile Çalıştır? Hangi ortam değişkenlerini ve parametreleri kullanmalıyım?

**Cevap:** YARN 'de Spark uygulamasını başlatmak için, ortam değişkenleri olarak belirtilmelidir `spark.yarn.appMasterEnv.[EnvironmentVariableName]` . Şunu kullanarak aşağıda bir örnek girin `spark-submit` :

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
* [Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama](debug.md)
