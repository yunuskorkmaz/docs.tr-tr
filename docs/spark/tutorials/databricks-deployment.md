---
title: Apache Spark uygulaması için Bir .NET'i Databricks'e dağıtma
description: Apache Spark uygulaması için bir .NET uygulamasını Databricks'e nasıl dağıtacağınızkeşfedin.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503968"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Öğretici: Databricks'e Apache Spark uygulaması için bir .NET dağıtma

Bu öğretici, tek tıklamayla kuruluma, kolaylaştırılmış iş akışlarına ve işbirliğine olanak tanıyan etkileşimli çalışma alanına sahip Apache Spark tabanlı bir analiz platformu olan Azure Databricks aracılığıyla uygulamanızı buluta nasıl dağıtacağınız öğretilir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> - Azure Databricks çalışma alanı oluşturun.
> - Apache Spark uygulaması için .NET'inizi yayınlayın.
> - Bir Kıvılcım iş ve Kıvılcım kümesi oluşturun.
> - Uygulamanızı Kıvılcım kümesinde çalıştırın.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdaki görevleri yapın:

* Azure hesabınız yoksa, ücretsiz bir [hesap](https://azure.microsoft.com/free/)oluşturun.
* [Azure portalında](https://portal.azure.com/)oturum açın.
* [Apache Spark için .NET](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) 'i tamamlayın - 10 Dakikalık eğitimde başlayın.

## <a name="create-an-azure-databricks-workspace"></a>Azure Databricks çalışma alanı oluşturma

> [!Note]
> Bu öğretici **Azure Ücretsiz Deneme Aboneliği**kullanılarak gerçekleştirilemez.
> Ücretsiz bir hesabınız varsa, profilinize gidin ve aboneliğinizi istediğiniz **kadar öde**olarak değiştirin. Daha fazla bilgi için bkz. [Ücretsiz Azure hesabı](https://azure.microsoft.com/free/). Ardından, [harcama sınırını kaldırın](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)ve bölgenizdeki VCPU'lar için kota artışı [isteyin.](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) Azure Databricks çalışma alanınızı oluşturduğunuzda, çalışma alanına ücretsiz Premium Azure Databricks DBUs'a 14 gün süreyle erişim sağlamak için **Deneme (Premium - 14 Gün Ücretsiz DBUs)** fiyatlandırma katmanını seçebilirsiniz.

Bu bölümde Azure portalını kullanarak bir Azure Databricks çalışma alanı oluşturursunuz.

1. Azure portalında, **bir kaynak** > Oluştur**Analytics** > **Azure Databricks'i**seçin.

   ![Azure portalında Bir Azure Databricks kaynağı oluşturma](./media/databricks-deployment/create-databricks-resource.png)

2. **Azure Databricks Hizmeti** bölümünde, Databricks çalışma alanı oluşturmak için değerler sağlayın.

    |Özellik  |Açıklama  |
    |---------|---------|
    |**Çalışma alanı adı**     | Databricks çalışma alanınız için bir ad sağlayın.        |
    |**Abonelik**     | Açılan listeden Azure aboneliğinizi seçin.        |
    |**Kaynak grubu**     | Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin. Kaynak grubu, bir Azure çözümü için ilgili kaynakları bir arada tutan kapsayıcıdır. Daha fazla bilgi için bkz. [Azure Kaynak Grubuna genel bakış](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Konum**     | Tercih ettiğiniz bölgeyi seçin. Kullanılabilir bölgeler hakkında bilgi için, [bölgeye göre kullanılabilen Azure hizmetlerine](https://azure.microsoft.com/regions/services/)bakın.        |
    |**Fiyatlandırma Katmanı**     |  **Standart,** **Premium**veya **Deneme**arasında seçim yapın. Bu katmanlar hakkında daha fazla bilgi için bkz. [Databricks fiyatlandırma sayfası](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Sanal Ağ**     |   Hayır       |

3. **Oluştur'u**seçin. Çalışma alanının oluşturulması birkaç dakika sürer. Çalışma alanı oluşturma sırasında, **Bildirimler'de**dağıtım durumunu görüntüleyebilirsiniz.

## <a name="install-azure-databricks-tools"></a>Azure Databricks araçlarını yükleme

Azure Databricks kümelerine bağlanmak ve yerel makinenizden dosyalar yüklemek için **Databricks CLI'yi** kullanabilirsiniz. Databricks, DBFS (Databricks Dosya Sistemi) aracılığıyla erişim dosyalarını kümeler.

1. Databricks CLI Python 3.6 veya üzeri gerektirir. Python zaten yüklüyse, bu adımı atlayabilirsiniz.

   **Windows için:**

   [Windows için Python'u İndirin](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Linux için:** Python çoğu Linux dağıtımında önceden yüklenmiş olarak gelir. Hangi sürümü yüklediğinizi görmek için aşağıdaki komutu çalıştırın:

   ```bash
   python3 --version
   ```

2. Databricks CLI'yi yüklemek için pip'i kullanın. Python 3.4 ve daha sonra varsayılan olarak pip içerir. Python 3 için pip3 kullanın. Şu komutu çalıştırın:

   ```bash
   pip3 install databricks-cli
   ```

3. Databricks CLI'yi yükledikten sonra, yeni bir komut istemi `databricks`açın ve komutu çalıştırın. Bir **'databricks'** alırsanız bir iç veya dış komut hatası olarak tanınmıyorsa, yeni bir komut istemi açtığınıza emin olun.

## <a name="set-up-azure-databricks"></a>Azure Veri Tuğlaları'nı ayarlama

Databricks CLI yüklü olduğundan, kimlik doğrulama ayrıntılarını ayarlamanız gerekir.

1. Databricks CLI komutunu `databricks configure --token`çalıştırın.

2. Yapılandırma komutunu çalıştırdıktan sonra, bir ana bilgisayar girmeniz istenir. Ana bilgisayar URL'niz şu biçimi kullanır: **https://<\Konum>.azuredatabricks.net**. Örneğin, Azure Databricks Hizmeti oluşturma sırasında **eastus2'yi** **https://eastus2.azuredatabricks.net**seçtiyseniz, ana bilgisayar .

3. Ana bilgisayarA girdikten sonra, bir belirteç girmeniz istenir. Azure portalında, Azure Veri Tuğlaları çalışma alanınızı başlatmak için **Çalışma Alanını Başlat'ı** seçin.

   ![Azure Databricks Çalışma Alanını Başlat](./media/databricks-deployment/launch-databricks-workspace.png)

4. Çalışma alanınızın ana sayfasında **Kullanıcı Ayarları'nı**seçin.

   ![Azure Databricks çalışma alanında kullanıcı ayarları](./media/databricks-deployment/databricks-user-settings.png)

5. Kullanıcı Ayarları sayfasında yeni bir belirteç oluşturabilirsiniz. Oluşturulan belirteci kopyalayın ve komut isteminize geri yapıştırın.

   ![Azure Databricks çalışma alanında yeni erişim belirteci oluşturma](./media/databricks-deployment/generate-token.png)

Artık oluşturduğunuz Azure Veri Tuğlaları kümelerine erişebilmeli ve DBFS'ye dosya yükleyebilmelisin.

## <a name="download-worker-dependencies"></a>Çalışan bağımlılıklarını karşıdan yükleme

1. Microsoft.Spark.Worker, yazdığınız kullanıcı tanımlı işlevler (UDF' ler) gibi Apache Spark'ın uygulamanızı yürütmesine yardımcı olur. [Microsoft.Spark.Worker'ı](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)karşıdan yükleyin.

2. *install-worker.sh,* Apache Spark bağımlı dosyaları için .NET'i kümenizin düğümlerine kopyalamanızı sağlayan bir komut dosyasıdır.

   Yerel bilgisayarınızda **install-worker.sh** adlı yeni bir dosya oluşturun ve GitHub'da bulunan [install-worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın.

3. *db-init.sh,* bağımlılıkları Databricks Spark kümenize yükleyen bir komut dosyasıdır.

   Yerel bilgisayarınızda **db-init.sh** adlı yeni bir dosya oluşturun ve GitHub'da bulunan [db-init.sh içeriğini](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) yapıştırın.

   Oluşturduğunuz dosyada değişkeni `DOTNET_SPARK_RELEASE` ' `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`ye göre ayarlayın. *db-init.sh* dosyanın geri kalanını olduğu gibi bırakın.

> [!Note]
> Windows kullanıyorsanız, *install-worker.sh* ve *db-init.sh* komut dosyalarınızdaki satır uçlarının Unix tarzı (LF) olduğundan doğrulayın. Not Defteri++ ve Atom gibi metin editörleri aracılığıyla satır sonlarını değiştirebilirsiniz.

## <a name="publish-your-app"></a>Uygulamanızı yayımlama

Ardından, Spark kümenizin uygulamanızı çalıştırmak için ihtiyaç duyduğu tüm dosyalara erişebilmesini sağlamak [için .NET for Apache Spark - Get in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) öğreticisinde oluşturulan *mySparkApp'ı* yayınlarsınız.

1. *mySparkApp'ı*yayınlamak için aşağıdaki komutları çalıştırın:

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Yayınlanan uygulama dosyalarınızı veri tuğlaları Kıvılcım kümenize kolayca yükleyebilmeniz için aşağıdaki görevleri yapın.

   **Windows'da:**

   mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64 adresinden ulaşın. Ardından, **Yayımla** klasörüne sağ tıklayın ve **> sıkıştırılmış (sıkıştırılmış) klasöre gönder'i**seçin. Yeni **klasörpublish.zip**adı .

   **Linux'ta aşağıdaki komutu çalıştırın:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Dosyaları karşıya yükleme

Bu bölümde, kümenizin uygulamanızı bulutta çalıştırmak için gereken her şeye sahip olması için DBFS'ye birkaç dosya yüklersiniz. DBFS'ye her dosya yüklediğinizde, bu dosyanın bilgisayarınızda bulunduğu dizinde olduğunuzdan emin olun.

1. *db-init.sh,* *install-worker.sh*ve *Microsoft.Spark.Worker'ı* DBFS'ye yüklemek için aşağıdaki komutları çalıştırın:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Kümeuygulamanızı çalıştırmak için gereken kalan dosyaları yüklemek için aşağıdaki komutları çalıştırın: sıkıştırılmış yayımlama klasörü, *input.txt*ve *microsoft-spark-2.4.x-0.3.0.jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Bir iş oluşturma

Uygulamanız, Apache **Spark**işleri için .NET'i çalıştırmak için kullandığınız komut olan kıvılcım gönder'i çalıştıran bir iş aracılığıyla Azure Databricks'te çalışır.

1. Azure Veri Tuğlaları Çalışma Alanınızda **İşler** simgesini seçin ve ardından **+ İş Oluştur'u**seçin.

   ![Azure Databricks işi oluşturma](./media/databricks-deployment/create-job.png)

2. İşiniz için bir başlık seçin ve ardından **kıvılcım gönder'i yapılandır'ı**seçin.

   ![Databricks işi için kıvılcım gönderme yapılandırma](./media/databricks-deployment/configure-spark-submit.png)

3. İş yapılandırmasında aşağıdaki parametreleri yapıştırın. Ardından, **Onayla'yı**seçin.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Küme oluşturma

1. İşinize gidin ve işinizin kümesini yapılandırmak için **Edit'i** seçin.

2. Kümenizi **Spark 2.4.1**olarak ayarlayın. Ardından, **Gelişmiş Seçenekler** > **Init Komut Dosyaları'nı**seçin. Komut Dosyası Yolunu `dbfs:/spark-dotnet/db-init.sh`' n için ayarla.

   ![Azure Veri Tuğlaları'nda kıvılcım kümesini yapılandırma](./media/databricks-deployment/cluster-config.png)

3. Küme ayarlarınızı onaylamak için **Onayla'yı** seçin.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. İşinize gidin ve yeni yapılandırılan Spark kümenizde işinizi çalıştırmak için **Şimdi Çalıştır'ı** seçin.

2. İş kümesinin oluşturması birkaç dakika sürer. Oluşturulduktan sonra, işiniz gönderilecektir ve çıktıyı görüntüleyebilirsiniz.

3. Sol menüden **Kümeler'i** ve ardından işinizin adını ve çalışmasını seçin.

4. İşinizin çıktısını görüntülemek için **Sürücü Günlükleri'ni** seçin. Uygulamanız yürütmeyi bitirdiğinde, standart çıktı konsoluna yazılan yerel çalıştırmaya başlarken aynı sözcük sayısı tablosunu görürsünüz.

   ![Azure Databricks iş çıktıtablosu](./media/databricks-deployment/table-output.png)

   Tebrikler, bulutta Apache Spark uygulaması için ilk .NET'inizi çalıştırdınız!

## <a name="clean-up-resources"></a>Kaynakları temizleme

Databricks çalışma alanına artık ihtiyacınız yoksa, Azure portalındaki Azure Veri Tuğlaları kaynağınızı silebilirsiniz. Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, .NET'inizi Apache Spark uygulaması için Databricks'e dağıttınız. Databricks hakkında daha fazla bilgi edinmek için Azure Veri Tuğlaları Dokümantasyonu'na devam edin.

> [!div class="nextstepaction"]
> [Azure Databricks Dokümantasyon](https://docs.microsoft.com/azure/azure-databricks/)
