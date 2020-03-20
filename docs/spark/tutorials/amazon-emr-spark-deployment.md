---
title: Amazon EMR Spark'a Apache Spark uygulaması için bir .NET dağıtın
description: Apache Spark uygulaması için Bir .NET uygulamasını Amazon EMR Spark'a nasıl dağıtacağınız keşfedin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73454941"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Amazon EMR Spark'a Apache Spark uygulaması için bir .NET dağıtın

Bu öğretici, Amazon EMR Spark'a Apache Spark uygulaması için bir .NET uygulamasının nasıl dağıtılanacağını öğretir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> * Microsoft.Spark.Worker'ı hazırlayın
> * Kıvılcım .NET uygulamanızı yayımlayın
> * Uygulamanızı Amazon EMR Spark'a dağıtın
> * Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdakileri yapın:

* [AWS CLI'yi](https://aws.amazon.com/cli/)indirin.
* [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) yerel makinenize indirin. Bu, Apache Spark bağımlı dosyaları için .NET'i daha sonra Spark kümenizin alt düğümlerine kopyalamak için kullandığınız yardımcı komut dosyasıdır.

## <a name="prepare-worker-dependencies"></a>Çalışan bağımlılıklarını hazırlama

**Microsoft.Spark.Worker,** Spark kümenizin tek tek alt düğümlerinde yaşayan bir arka uç bileşenidir. Bir C# UDF (kullanıcı tanımlı işlev) yürütmek istediğinizde, Spark'ın UDF'yi yürütmek için .NET CLR'yi nasıl başlatabileceğinizi anlaması gerekir. **Microsoft.Spark.Worker,** Spark'a bu işlevselliği sağlayan bir sınıf koleksiyonu sağlar.

1. Kümenizde dağıtılacak bir [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.

   Örneğin, kullanmak `.NET for Apache Spark v0.1.0` `netcoreapp2.1`istiyorsanız, [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)indirirsiniz.

2. Kümenizin erişebilen dağıtılmış bir dosya sistemine (örneğin, S3) yükleyin `Microsoft.Spark.Worker.<release>.tar.gz` ve [install-worker.sh.](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)

## <a name="prepare-your-net-for-apache-spark-app"></a>.NET'inizi Apache Spark uygulamasına hazırlayın

1. Uygulamanızı oluşturmak için [Başlangıç](get-started.md) öğretisini izleyin.

2. Spark .NET uygulamanızı bağımsız olarak yayımlayın.

   Linux üzerinde aşağıdaki komutu çalıştırın.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Yayınlanan `<your app>.zip` dosyalar için üretin.

   Kullanarak Linux üzerinde aşağıdaki `zip`komutu çalıştırın.

   ```bash
   zip -r <your app>.zip .
   ```

4. Kümenizin erişebilen dağıtılmış bir dosya sistemine (örneğin, S3) aşağıdaki öğeleri yükleyin:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu kavanoz [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahildir ve uygulamanızın yapı çıktı dizini nde yer alır.
   * `<your app>.zip`
   * Her çalışanın erişebileceği bağımlılık dosyaları (bağımlılık dosyaları veya her çalışanın erişebileceği yaygın veriler gibi) veya derlemeler (uygulamanızın bağlı olduğu kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren DL'ler gibi) her uygulayıcının çalışma dizinine yerleştirilir.

## <a name="deploy-to-amazon-emr-spark"></a>Amazon EMR Spark'a dağıtın

[Amazon EMR,](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) AWS'de büyük veri çerçevelerinin çalıştırAn basitleştiren yönetilen bir küme platformudur.

> [!NOTE]
> Amazon EMR Spark Linux tabanlıdır. Bu nedenle, uygulamanızı Amazon EMR Spark'a dağıtmak istiyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini kullandığınızdan](https://dotnet.microsoft.com/download) emin olun.

### <a name="deploy-microsoftsparkworker"></a>Microsoft.Spark.Worker'ı dağıtma

Bu adım yalnızca küme oluşturma da gereklidir.

`install-worker.sh` [Bootstrap Eylemleri](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)kullanarak küme oluşturma sırasında çalıştırın.

AWS CLI kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.

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

Uygulamanızı Amazon EMR Spark'ta çalıştırmanın iki yolu vardır: kıvılcım gönderme ve Amazon EMR Adımları.

### <a name="use-spark-submit"></a>Kıvılcım gönder'i kullanma

Apache Spark işleri için .NET'i Amazon EMR Spark'a göndermek için [kıvılcım gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.

1. `ssh`kümedeki düğümlerden birine.

2. `spark-submit` öğesini çalıştırın.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Amazon EMR Adımlarını Kullan

[Amazon EMR Adımları,](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) EMR kümesine yüklenen Spark çerçevesine iş göndermek için kullanılabilir.

AWS CLI kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, Apache Spark uygulaması için .NET'inizi Amazon EMR Spark'a dağıttınız. Apache Spark örnek projeleri için .NET için GitHub'a devam edin.

> [!div class="nextstepaction"]
> [.Net Apache Spark örnekleri için](https://github.com/dotnet/spark/tree/master/examples)
