---
title: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı
description: Databricks 'e Apache Spark uygulamasının bir .NET uygulamasını nasıl dağıtacağınızı öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "69577061"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı

Bu öğreticide, Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
> * Microsoft. spark. Worker 'ı hazırla
> * Spark .NET uygulamanızı yayımlama
> * Uygulamanızı Databricks 'e dağıtın
> * Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdakileri yapın:

* [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)'yi indirin.
* [İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin. Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.

## <a name="prepare-worker-dependencies"></a>Çalışan bağımlılıklarını hazırlama

**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir. Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ıN, UDF 'yi yürütmek IÇIN .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir. **Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.

1. Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.

   Örneğin, kullanmak `.NET for Apache Spark v0.1.0` `netcoreapp2.1`istiyorsanız [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.

2. Kümenizin `Microsoft.Spark.Worker.<release>.tar.gz` erişimi olan bir dağıtılmış dosya sistemine (örneğin, dBFS) yükleyin ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) .

## <a name="prepare-your-net-for-apache-spark-app"></a>Apache Spark uygulamanızı .NET 'e hazırlama

1. Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.

2. Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.

   Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Yayımlanan `<your app>.zip` dosyalar için üretin.

   Kullanarak `zip`Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.

   ```bash
   zip -r <your app>.zip .
   ```

4. Aşağıdakileri kümenizin erişimi olan bir dağıtılmış dosya sistemine (örneğin, DBFS) yükleyin:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.
   * `<your app>.zip`
   * Her bir yürütücünün çalışma dizinine yerleştirilmesi için dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler gibi) veya derlemeler (Kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren dll 'Ler gibi).

## <a name="deploy-to-databricks"></a>Databricks’e dağıtma

[Databricks](https://databricks.com) , Apache Spark kullanarak bulut tabanlı büyük veri işleme sağlayan bir platformdur.

> [!Note] 
> [Azure Databricks](https://azure.microsoft.com/services/databricks/) ve [AWS Databricks](https://databricks.com/aws) , Linux tabanlıdır. Bu nedenle, uygulamanızı Databricks 'e dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisi](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.

Databricks, mevcut bir etkin kümeye .NET Apache Spark uygulamaları göndermenize veya bir işi her başlattığınızda yeni bir küme oluşturmanıza olanak sağlar. Bu, bir .NET Apache Spark uygulaması göndermeden önce **Microsoft. spark. Worker** 'ın yüklenmesini gerektirir.

### <a name="deploy-microsoftsparkworker"></a>Microsoft. spark. Worker 'ı dağıtma

Bu adım, bir küme için yalnızca bir kere gereklidir.

1. [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) ve install-Worker.sh [](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) 'i yerel makinenize indirin.

2. **DB-init.sh** öğesini, kümenize indirmek ve yüklemek istediğiniz **Microsoft. spark. Worker** sürümüne işaret etmek üzere değiştirin.

3. [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)'yı yükler.

4. Databricks CLı için [kimlik doğrulama ayrıntılarını ayarlayın](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) .

5. Aşağıdaki komutu kullanarak dosyaları Databricks kümenize yükleyin:

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Databricks çalışma alanınıza gidin. Sol taraftaki menüden **kümeler** ' ı seçin ve ardından **küme oluştur**' u seçin.

7. Kümeyi uygun şekilde yapılandırdıktan sonra, **Init betiğini** ayarlayın ve kümeyi oluşturun.

   ![Betik eylemi resmi](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>Uygulamanızı çalıştırma 

İşinizi databricks `spark-submit` 'e göndermek için ya da kullanabilirsiniz `set JAR` .

### <a name="use-set-jar"></a>Set JAR kullanın

[Set jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) , mevcut bir etkin kümeye bir iş göndermenize olanak tanır.

#### <a name="one-time-setup"></a>Tek seferlik kurulum

1. Databricks kümenize gidin ve sol taraftaki menüden **işler** ' i seçin. Ardından **kavanı ayarla**' yı seçin.

2. Uygun `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` dosyayı karşıya yükleyin.

3. Parametreleri uygun şekilde ayarlayın.

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. **Kümeyi** , önceki bölümde Için **Init betiğini** oluşturduğunuz var olan kümeye işaret etmek üzere yapılandırın.

#### <a name="publish-and-run-your-app"></a>Uygulamanızı yayımlayın ve çalıştırın

1. Uygulamanızı Databricks kümenize yüklemek için [DATABRICKS CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) kullanın.

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. Bu adım yalnızca, uygulama derlemelerinizin (örneğin, bağımlılıklarıyla birlikte Kullanıcı tanımlı işlevler içeren dll 'Ler) her **Microsoft. spark. Worker**çalışma dizinine yerleştirilmesi gereken durumlarda gereklidir.

   - Uygulama derlemelerinizi Databricks kümenize yükleyin
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) ' deki uygulama bağımlılıkları bölümünü Açıklama penceresinde, uygulama bağımlılıkları yolunu işaret edin ve Databricks kümenize yükleyin.
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - Kümenizi yeniden başlatın.

3. Databricks çalışma alanınızdaki Databricks kümenize gidin. **İşler**altında işiniz ' ı seçin ve ardından işi çalıştırmak Için **Şimdi Çalıştır** ' ı seçin.

### <a name="use-spark-submit"></a>Spark-gönder kullan

[Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutu, bir işi yeni bir kümeye göndermenize olanak tanır.

1. [Bir Iş oluşturun](https://docs.databricks.com/user-guide/jobs.html) ve **Spark-gönder**' i seçin.

2. Aşağıdaki `spark-submit` parametrelerle yapılandırın:

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. Databricks çalışma alanınızdaki Databricks kümenize gidin. **İşler**altında işiniz ' ı seçin ve ardından işi çalıştırmak Için **Şimdi Çalıştır** ' ı seçin.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Apache Spark için .NET uygulamanızı Databricks 'e dağıttınız. Databricks hakkında daha fazla bilgi edinmek için Azure Databricks belgelerine ilerleyin.

> [!div class="nextstepaction"]
> [Azure Databricks belgeleri](https://docs.microsoft.com/azure/azure-databricks/)
