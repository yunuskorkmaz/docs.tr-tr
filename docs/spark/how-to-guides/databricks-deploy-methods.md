---
title: Databricks 'e Apache Spark iş için .NET gönderme
description: Spark-gönder ve ayarla jar kullanarak Databricks 'e yönelik bir .NET Apache Spark işi göndermeyi öğrenin.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9cd3d40871d4600660957ec268f192ef3e045845
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838353"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Databricks 'e Apache Spark iş için .NET gönderme

Apache Spark iş için .NET uygulamanızı Databricks 'e dağıtmanın iki yolu vardır: `spark-submit` ve set jar. 

## <a name="deploy-using-spark-submit"></a>Spark-gönder kullanarak dağıtma

Apache Spark işleri için .NET 'i Databricks 'e göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz. `spark-submit` yalnızca istek üzerine oluşturulmuş bir kümeye gönderim yapılmasına izin verir.

1. Databricks çalışma alanınıza gidin ve bir iş oluşturun. İşiniz için bir başlık seçin ve ardından **Spark-gönder**' i seçin. Aşağıdaki parametreleri iş yapılandırmasına yapıştırın ve **Onayla**' yı seçin.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Yukarıdaki parametrenin içeriğini, belirli dosyalarınıza ve yapılandırmanıza göre güncelleştirin. Örneğin, DBFS 'ye yüklediğiniz Microsoft. Spark jar dosyasının sürümüne başvurun ve uygulamanızın uygun adını ve yayımlanmış uygulama ZIP dosyasını kullanın.

2. İşinizin kümesini yapılandırmak için işinize gidin ve **Düzenle** ' yi seçin. Dağıtımınızda kullanmak istediğiniz Apache Spark sürümüne göre Databricks Runtime sürümünü ayarlayın. Ardından **Init betikleri > gelişmiş seçenekler**' i seçin ve Init betiği yolunu `dbfs:/spark-dotnet/db-init.sh`olarak ayarlayın. Küme ayarlarınızı onaylamak için **Onayla** ' yı seçin.

3. İşinizi yeni yapılandırılmış Spark kümenizde çalıştırmak için işinize gidin ve **Şimdi Çalıştır** ' ı seçin. İş kümesinin oluşturulması birkaç dakika sürer. Oluşturulduktan sonra işiniz gönderilir. Databricks çalışma alanınızın sol menüsünde **kümeler** ' ı seçerek çıktıyı görüntüleyebilir, ardından **sürücü günlükleri**' ni seçebilirsiniz.

## <a name="deploy-using-set-jar"></a>Set jar kullanarak dağıtma

Alternatif olarak, databricks 'e Apache Spark işleri için .NET göndermek üzere Databricks çalışma alanınızda [set jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) öğesini kullanabilirsiniz. *Set jar* , mevcut bir etkin kümeye iş gönderilmesini sağlar.

### <a name="one-time-setup"></a>Tek seferlik kurulum

1. Databricks kümenize gidin ve sol taraftaki menüden **işler** ' i ve ardından **jar ayarla**' yı seçin.

2. Uygun `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`yükleyin.

3. Aşağıdaki parametreleri `<your-app-name>`yerine yayımladığınız yürütülebilir dosya için doğru adı içerecek şekilde değiştirin:

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Kümeyi, zaten init betiğini ayarlamış olduğunuz mevcut bir kümeye işaret etmek üzere yapılandırın.

### <a name="publish-and-run-your-app"></a>Uygulamanızı yayımlayın ve çalıştırın

1. Uygulamanızı yayımladığınızdan ve uygulama kodunuzun `SparkSession.Stop()`kullanmadığından emin olun.

2. Uygulamanızı Databricks kümenize yüklemek için [DATABRICKS CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) kullanın. Örneğin, yayımlanmış uygulamanızı kümenize yüklemek için aşağıdaki komutu kullanın:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Uygulamanızda Kullanıcı tanımlı işlevleriniz varsa, bağımlılıklarıyla birlikte Kullanıcı tanımlı işlevler içeren dll 'Ler gibi uygulama derlemelerinin her bir *Microsoft. spark. Worker*çalışma dizinine yerleştirilmesi gerekir.

    Uygulama derlemelerinizi Databricks kümenize yükleyin:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) ' deki uygulama bağımlılıkları bölümünü açıklama olarak değiştirin ve uygulama bağımlılıkları yolunu işaret edin. Ardından, güncelleştirilmiş *DB-init.sh* , kümenize yükleyin:

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. İşi çalıştırmak için **Şimdi çalıştırın > Databricks kümesi > işler > [iş-adı] Şimdi Çalıştır** .

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı](../tutorials/databricks-deployment.md)
* [Azure Databricks belgeleri](https://docs.microsoft.com/azure/azure-databricks/)
