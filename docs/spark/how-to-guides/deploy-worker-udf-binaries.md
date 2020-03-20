---
title: Apache Spark işçisi ve kullanıcı tanımlı işlev ikilileri için .NET'i dağıtma
description: Apache Spark çalışanı ve kullanıcı tanımlı işlev ikilileri için .NET'i nasıl dağıtacağınız hakkında bilgi edinin.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f373ccee398149adcadeac91f02d9896214706b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187590"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Apache Spark işçisi ve kullanıcı tanımlı işlev ikilileri için .NET'i dağıtma

Bu nasıl yapılacağına ilişkin genel yönergeler, Apache Spark çalışanı ve kullanıcı tanımlı işlev ikilileri için .NET'in nasıl dağıtılanacağına ilişkin genel yönergeler sağlar. Hangi Çevre Değişkenlerinin ayarlanacaGIni ve uygulamaları başlatmak için sıkça kullanılan bazı parametreleri `spark-submit`öğrenirsiniz.

## <a name="configurations"></a>Yapılandırmalar
Yapılandırmalar, Apache Spark işçi ve kullanıcı tanımlı işlev ikilileri için .NET dağıtmak için genel ortam değişkenlerini ve parametrelerayarlarını gösterir.

### <a name="environment-variables"></a>Ortam değişkenleri
Çalışanları dağıtırken ve UDF yazarken, ayarlamanız gereken birkaç yaygın olarak kullanılan ortam değişkeni vardır:

| Çevre Değişkeni         | Açıklama
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | İkilinin <code>Microsoft.Spark.Worker</code> oluşturulduğu yol.</br>Spark sürücüsü tarafından kullanılır ve Kıvılcım uygulayıcılarına geçer. Bu değişken ayarlanmamışsa, Kıvılcım uygulayıcıları ortam değişkeninde <code>PATH</code> belirtilen yolu ararlar.</br>_örneğin: "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Derlemeleri <code>Microsoft.Spark.Worker</code> yükleyeceğimvir ayrılmış yollar.</br>Bir yol "."ile başlarsa, çalışma dizininin hazır olacağını unutmayın. Eğer **iplik modunda**ise , "." konteynerin çalışma dizini temsil eder.</br>_örneğin"C:\Kullanıcılar\\&lt;kullanıcı adı&gt;\\&lt;mysparkapp&gt;\bin\Hata\\&lt;ayıklama&gt;dotnet sürümü "_
| DOTNET_WORKER_DEBUG          | <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">Bir UDF hata ayıklamak</a>istiyorsanız, çalıştırmadan <code>1</code> <code>spark-submit</code>önce bu ortam değişkenini ayarlayın.

### <a name="parameter-options"></a>Parametre seçenekleri
Spark uygulaması [paketledikten](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)sonra, kullanarak `spark-submit`başlatabilirsiniz. Aşağıdaki tablo, sık kullanılan seçeneklerden bazılarını gösterir:

| Parametre Adı        | Açıklama
| :---------------------| :----------
| --sınıf               | Başvurunuzun giriş noktası.</br>_örneğin org.apache.spark.deploy.dotnet.DotnetRunner_
| --usta              | Kümenin ana URL'si. <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">master URL</a></br>_örneğin iplik_
| --deploy-mode         | Sürücünüzü işçi düğümlerine ( )<code>cluster</code>mi yoksa yerel olarak<code>client</code>harici istemci olarak mı dağıtacaksın ( ).</br>Varsayılan:<code>client</code>
| --conf                | Biçimde <code>key=value</code> rasgele Spark yapılandırma özelliği.</br>_örneğin spark.iplikn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_
| --dosyalar               | Her uygulayıcının çalışma dizinine yerleştirilecek dosyaların virgülle ayrılmış listesi.<br/><ul><li>Bu seçeneğin sadece iplik modu için geçerli olduğunu lütfen unutmayın.</li><li>Hadoop'a benzer # ile dosya adlarını belirtmeyi destekler.</br></ul>_örneğin <code>myLocalSparkApp.dll#appSeen.dll</code>. Uygulamanız, İplik <code>appSeen.dll</code> üzerinde <code>myLocalSparkApp.dll</code> çalışırken başvuru olarak adı kullanmalıdır._</li>
| --arşiv          | Her uygulayıcının çalışma dizinine çıkarılacak arşivlerin virgülden ayrılmış listesi.</br><ul><li>Bu seçeneğin sadece iplik modu için geçerli olduğunu lütfen unutmayın.</li><li>Hadoop'a benzer # ile dosya adlarını belirtmeyi destekler.</br></ul>_örneğin <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. Bu, zip dosyasını kopyalar ve klasöre <code>worker</code> çıkarır._</li>
| uygulama-kavanoz       | Uygulamanız ve tüm bağımlılıkları içeren paketlenmiş bir kavanoza giden yol.</br>_örneğin&lt;kavanozunuza&gt;hdfs:// yol /microsoft-kıvılcım-&lt;sürüm&gt;.jar_
| uygulama bağımsız değişkenleri | Varsa ana sınıfınızın ana yöntemine geçirilen bağımsız değişkenler.</br>_&lt;örneğin uygulamanıza&gt;/&lt;giden hdfs:// yol&gt;.zip &lt;uygulamanız&gt; &lt;ad uygulaması args&gt;_

> [!NOTE]
> Uygulamaları başlatırken `application-jar` tüm öncekileri `spark-submit` `--options` belirtin , aksi takdirde bunlar yoksayılır. Daha fazla bilgi için, [ `spark-submit` İplik](https://spark.apache.org/docs/latest/submitting-applications.html) ayrıntıları seçenekleri ve [çalışan kıvılcım](https://spark.apache.org/docs/latest/running-on-yarn.html)bakın.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>UDF'ler ile bir kıvılcım uygulaması çalıştırdığımda, bir 'FileNotFoundException' hatası alıyorum. Ne yapmalıyım?
> **Hata:** [Hata] [TaskRunner] [0] ProcessStream() istisnasız başarısız oldu: System.IO.FileNotFoundException: Assembly 'mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' dosyası bulunamadı: 'mySparkApp.dll'

**Cevap:** Ortam değişkeninin `DOTNET_ASSEMBLY_SEARCH_PATHS` doğru ayarlıp ayarlıldığını denetleyin. Senin. `mySparkApp.dll`

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Apache Spark sürümü için .NET'imi `DOTNET_WORKER_DIR` yükselttikten ve ortam değişkenini `IOException` sırdadıktan sonra neden hala aşağıdaki hatayı alıyorum?
> **Hata:** 11.0 (TID 24, localhost, executor driver): java.io.IOException: "Microsoft.Spark.Worker.exe" programını çalıştıramıyor: CreateProcess hatası=2, Sistem belirtilen dosyayı bulamıyor.

**Cevap:** En son ortam değişken değerlerini alabilmek için önce PowerShell pencerenizi (veya diğer komut pencerelerini) yeniden başlatmayı deneyin. O zaman programınızı başlatın.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Benim Kıvılcım uygulama gönderdikten sonra, `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`hata olsun.
> **Hata:** [Hata] [TaskRunner] [0] ProcessStream() istisnadışında başarısız oldu: System.TypeLoadException: 'System.Runtime.Remoting.Contexts.Context' türünü yüklemedi montaj 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...'.

**Cevap:** Kullandığınız `Microsoft.Spark.Worker` sürümü kontrol edin. İki versiyonu vardır: **.NET Framework 4.6.1** ve **.NET Core 2.1.x**. Bu durumda, `Microsoft.Spark.Worker.net461.win-x64-<version>` [(indirebilirsiniz)](https://github.com/dotnet/spark/releases)sadece .NET `System.Runtime.Remoting.Contexts.Context` Framework için olduğu için kullanılmalıdır.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Kıvılcım uygulamamı İplik'te UDF'lerle nasıl çalıştırıyorum? Hangi ortam değişkenlerini ve parametrelerini kullanmalıyım?

**Cevap:** Kıvılcım uygulamasını İplik üzerinde başlatmak için ortam değişkenleri `spark.yarn.appMasterEnv.[EnvironmentVariableName]`olarak belirtilmelidir. Lütfen aşağıdaki örneği kullanarak `spark-submit`bakın:

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

* [Apache Spark için .NET ile başlayın](../tutorials/get-started.md)
* [Windows'da Apache Spark uygulaması için bir .NET hata ayıklama](../how-to-guides/debug.md)
