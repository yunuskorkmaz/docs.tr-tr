---
title: Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma
description: Apache Spark uygulamasının bir .NET uygulamasını Amazon EMR Spark 'a dağıtmayı öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bf52a53e8f282f55a0071deb266dabb798fa3348
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254058"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma

Bu öğreticide, Amazon EMR Spark 'a Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
> * Microsoft. spark. Worker 'ı hazırla
> * Spark .NET uygulamanızı yayımlama
> * Uygulamanızı Amazon EMR Spark 'a dağıtın
> * Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdakileri yapın:

* [AWS CLI](https://aws.amazon.com/cli/)'yi indirin.
* [İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin. Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.

## <a name="prepare-worker-dependencies"></a>Çalışan bağımlılıklarını hazırlama

**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir. Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ıN, UDF 'yi yürütmek IÇIN .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir. **Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.

1. Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.

   Örneğin, kullanmak `.NET for Apache Spark v0.1.0` `netcoreapp2.1`istiyorsanız [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.

2. Kümenizin `Microsoft.Spark.Worker.<release>.tar.gz` erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) .

## <a name="prepare-your-net-for-apache-spark-app"></a>Apache Spark uygulamanızı .NET 'e hazırlama

1. Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.

2. Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.

   Linux üzerinde aşağıdaki komutu çalıştırın.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Yayımlanan `<your app>.zip` dosyalar için üretin.

   Kullanarak `zip`Linux üzerinde aşağıdaki komutu çalıştırın.

   ```bash
   zip -r <your app>.zip .
   ```

4. Aşağıdaki öğeleri, kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.
   * `<your app>.zip`
   * Her bir yürütücünün çalışma dizinine yerleştirilmesi için dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler gibi) veya derlemeler (Kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren dll 'Ler gibi).

## <a name="deploy-to-amazon-emr-spark"></a>Amazon EMR Spark 'a dağıtın

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) , AWS 'de büyük veri çerçevelerini çalıştırmayı kolaylaştıran bir yönetilen küme platformudur.

> [!NOTE] 
> Amazon EMR Spark, Linux tabanlıdır. Bu nedenle, uygulamanızı Amazon EMR Spark 'a dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.

### <a name="deploy-microsoftsparkworker"></a>Microsoft. spark. Worker 'ı dağıtma

Bu adım yalnızca küme oluşturulurken gereklidir.

`install-worker.sh` [Önyükleme eylemlerini](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)kullanarak küme oluşturma sırasında çalıştırın.

AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

Bu uygulamayı Amazon EMR Spark: Spark-gönderme ve Amazon EMR adımlarında çalıştırmanın iki yolu vardır.

### <a name="use-spark-submit"></a>Spark-gönder kullan

[Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanarak, Amazon emr spark 'a Apache Spark işleri için .net gönderebilirsiniz.

1. `ssh`Kümedeki düğümlerden birine.

2. `spark-submit`'i çalıştırın.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Amazon EMR adımlarını kullanma

[Amazon emr adımları](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) , BIR ışı emr kümesinde yüklü Spark çerçevesine göndermek için kullanılabilir.

AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Apache Spark için .NET uygulamanızı Amazon EMR Spark 'a dağıttınız. Apache Spark örnek projelerine yönelik .NET için GitHub ' a devam edin.

> [!div class="nextstepaction"]
> [Apache Spark örnekleri için .NET](https://github.com/dotnet/spark/tree/master/examples)
