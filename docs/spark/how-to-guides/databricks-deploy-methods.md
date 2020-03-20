---
title: Databricks'e Apache Spark işi için bir .NET gönderme
description: Spark gönder ve Jar'ı Ayarla'yı kullanarak Databricks'e Apache Spark için bir .NET işini nasıl göndereceğinizi öğrenin.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187604"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Databricks'e Apache Spark işi için bir .NET gönderme

Apache Spark için .NET işinizi Databricks'e `spark-submit` dağıtmanın iki yolu vardır: ve Jar'ı Ayarlayın.

## <a name="deploy-using-spark-submit"></a>Kıvılcım gönder'i kullanarak dağıtma

Apache [Spark](https://spark.apache.org/docs/latest/submitting-applications.html) işleri için .NET'i Databricks'e göndermek için kıvılcım gönder komutunu kullanabilirsiniz. `spark-submit`yalnızca isteğe bağlı oluşturulan bir kümeye gönderilmesine izin verir.

1. Databricks Çalışma Alanınıza gidin ve bir iş oluşturun. İşiniz için bir başlık seçin ve ardından **kıvılcım gönder'i yapılandır'ı**seçin. İş yapılandırmasında aşağıdaki parametreleri yapıştırın ve **onayla'yı**seçin.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Yukarıdaki parametrenin içeriğini özel dosyalarınıza ve yapılandırmanıza göre güncelleştirin. Örneğin, DBFS'ye yüklediğiniz Microsoft.Spark kavanoz dosyasının sürümüne başvurun ve uygulamanızın uygun adını ve yayınlanan uygulama zip dosyasını kullanın.

2. İşinize gidin ve işinizin kümesini yapılandırmak için **Edit'i** seçin. Databricks Runtime Sürümünü, dağıtımınızda kullanmak istediğiniz Apache Spark sürümünü temel alın. Ardından **Gelişmiş Seçenekler > Init Komut Dosyaları'nı** `dbfs:/spark-dotnet/db-init.sh`seçin ve Komut Dosyası Yolunu 'da ' olarak ayarlayın. Küme ayarlarınızı onaylamak için **Onayla'yı** seçin.

3. İşinize gidin ve yeni yapılandırılan Spark kümenizde işinizi çalıştırmak için **Şimdi Çalıştır'ı** seçin. İş kümesinin oluşturulması birkaç dakika sürer. Oluşturulduktan sonra, işiniz sunulacaktır. Databricks çalışma alanınızın sol menüsünden **Kümeler'i** seçerek çıktıyı görüntüleyebilir, ardından **Sürücü Günlükleri'ni**seçebilirsiniz.

## <a name="deploy-using-set-jar"></a>Set Jar'ı kullanarak dağıtma

Alternatif olarak, Apache Spark işleri için .NET'i Databricks'e göndermek için Databricks çalışma alanınızdaki [Set Jar'ı](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) kullanabilirsiniz. *Set Jar* varolan bir etkin kümeye iş gönderme sağlar.

### <a name="one-time-setup"></a>Tek seferlik kurulum

1. Databricks kümenize gidin ve sol taraftaki menüden **İş'leri** seçin ve ardından **JAR'ı ayarlayın.**

2. Yükleme uygun `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.

3. Aşağıdaki parametreleri, aşağıdaki ler yerine yayınladığınız yürütülebilir `<your-app-name>`için doğru adı içerecek şekilde değiştirin:

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Kümeyi, init komut dosyasını zaten ayarlamış olduğunuz varolan bir kümeye işaret etmek üzere yapılandırın.

### <a name="publish-and-run-your-app"></a>Uygulamanızı yayımlayın ve çalıştırın

1. Uygulamanızı yayımladığınızdan ve uygulama kodunuzu kullanmadığınızdan `SparkSession.Stop()`emin olun.

2. Uygulamanızı Databricks kümenize yüklemek için [Databricks CLI'yi](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) kullanın. Örneğin, yayınlanan uygulamanızı kümenize yüklemek için aşağıdaki komutu kullanın:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Uygulamanızda kullanıcı tanımlı işlevleriniz varsa, kullanıcı tanımlı işlevleri ve bağımlılıkları içeren DL'ler gibi uygulama derlemelerinin her *Microsoft.Spark.Worker'ın*çalışma dizinine yerleştirilmesi gerekir.

    Uygulama derlemelerinizi Databricks kümenize yükleyin:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Uygulama bağımlılıkları yolunuza işaret etmek için [db-init.sh'daki](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) uygulama bağımlılıkları bölümünü açıklamave değiştirin. Ardından, güncelleştirilmiş *db-init.sh* kümenize yükleyin:

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. İşinizi çalıştırmak için **Şimdi Çalıştır'> Iş > [İş adı] > Databricks kümesine** gidin.

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile başlayın](../tutorials/get-started.md)
* [Apache Spark uygulaması için Bir .NET'i Databricks'e dağıtma](../tutorials/databricks-deployment.md)
* [Azure Databricks Dokümantasyon](https://docs.microsoft.com/azure/azure-databricks/)
