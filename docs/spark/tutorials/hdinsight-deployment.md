---
title: Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma
description: Apache Spark uygulaması için bir .NET uygulamasını HDInsight'a nasıl dağıtacağınız keşfedin.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504168"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Öğretici: Apache Spark uygulaması için Bir .NET uygulamasını Azure HDInsight'a dağıtma

Bu öğretici, Bir Azure HDInsight kümesi aracılığıyla .NET for Apache Spark uygulamanızı buluta nasıl dağıtacağınız öğretilir. HDInsight'taki Spark kümeleri Azure Depolama ve Azure Veri Gölü Depolama ile uyumlu olduğundan HDInsight, Azure'da bir Kıvılcım kümesi oluşturmayı ve yapılandırmayı kolaylaştırır.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> * Azure Depolama Gezgini'ni kullanarak depolama hesaplarınıza erişin.
> * Azure HDInsight kümesi oluşturun.
> * Apache Spark uygulaması için .NET'inizi yayınlayın.
> * HDInsight komut dosyası eylemi oluşturun ve çalıştırın.
> * Bir HDInsight kümesinde Apache Spark uygulaması için bir .NET çalıştırın.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdaki görevleri yapın:

* Azure aboneliğiniz yoksa, ücretsiz bir [hesap](https://azure.microsoft.com/free/)oluşturun.
* [Azure portalında](https://portal.azure.com/)oturum açın.
* Azure Depolama Gezgini'ni [Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)veya [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) bilgisayarınıza yükleyin.
* [Apache Spark için .NET](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) 'i tamamlayın - 10 Dakikalık eğitimde başlayın.

## <a name="access-your-storage-accounts"></a>Depolama hesaplarınıza erişin

1. Azure Depolama Gezgini'ni açın.

2. Sol menüde **Hesap Ekle'yi** seçin ve Azure hesabınızda oturum açın.

    ![Depolama Gezgini'nden Azure hesabında oturum açma](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Oturum açmadan sonra, sahip olduğunuz tüm depolama hesaplarını ve depolama hesaplarınıza yüklediğiniz kaynakları görmeniz gerekir.

## <a name="create-an-hdinsight-cluster"></a>HDInsight kümesi oluşturma

> [!IMPORTANT]
> HDInsight kümelerinin faturalandırması, kullanmasanız bile dakika başına eşit olarak dağılır. Kullanmayı bitirdikten sonra kümenizi sildiğinizden emin olun. Daha fazla bilgi için bu öğreticinin [kaynakları temizle](#clean-up-resources) bölümüne bakın.

1. Azure [portalını](https://portal.azure.com)ziyaret edin.

2. **+ Kaynak oluştur**’u seçin. Ardından, **Analytics** kategorisinden **HDInsight'ı** seçin.

    ![Azure portalından HDInsight kaynağı oluşturma](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. **Temel Bilgiler** bölümünde aşağıdaki değerleri sağlayın:

    |Özellik  |Açıklama  |
    |---------|---------|
    |Abonelik  | Açılan noktadan, etkin Azure aboneliklerinizden birini seçin. |
    |Kaynak grubu | Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin. Kaynak grubu, bir Azure çözümü için ilgili kaynakları bir arada tutan kapsayıcıdır. |
    |Küme adı | HDInsight Spark kümenize bir ad verin.|
    |Konum   | Kaynak grubu için bir konum seçin. Şablon hem kümeyi oluşturmak için hem de varsayılan küme depolaması için bu konumu kullanır. |
    |Küme türü| Küme türü olarak **Spark'ı** seçin.|
    |Küme sürümü|Küme türü seçildikten sonra bu alan varsayılan sürümle otomatik doldurulur. Kıvılcım'ın 2.3 veya 2.4 sürümünü seçin.|
    |Küme oturum açma kullanıcı adı| Küme oturum açma kullanıcı adını girin.  Varsayılan ad, *admin* şeklindedir. |
    |Küme oturum açma parolası| Herhangi bir giriş parolası girin. |
    |Secure Shell (SSH) kullanıcı adı| SSH kullanıcı adını girin. Varsayılan olarak bu hesap, *Küme Oturum Açma kullanıcı adı* hesabıyla aynı parolayı paylaşır. |

4. **Sonraki'ni seçin:** **Depolama** sayfasına devam etmek için Depolama >>. **Depolama** bölümünde aşağıdaki değerleri sağlayın:

    |Özellik  |Açıklama  |
    |---------|---------|
    |Birincil depolama türü|Varsayılan değeri kullanın **Azure Depolama**.|
    |Seçim yöntemi|Varsayılan değeri kullanın **Listeden seçin.**|
    |Birincil depolama hesabı|Aboneliğinizi ve bu abonelik içindeki etkin depolama hesaplarınızdan birini seçin.|
    |Kapsayıcı|Bu kapsayıcı, kümenizin uygulamanızı bulutta çalıştırmak için dosyaları aradığı depolama hesabınızdaki özel blob kapsayıcısır. Herhangi bir kullanılabilir ad verebilirsiniz.|

5. **İnceleme altında + oluştur**, **Oluştur'u**seçin. Kümenin oluşturulması yaklaşık 20 dakika sürer. Bir sonraki adıma devam etmeden önce kümenin oluşturulması gerekir.

## <a name="publish-your-app"></a>Uygulamanızı yayımlama

Ardından, [Apache Spark için .NET'te](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) oluşturulan *mySparkApp'ı* yayınlarsınız - 10 Dakikalık eğitimde başlayın, bu da Spark kümenize uygulamanızı çalıştırmak için gereken tüm dosyalara erişim sağlar.

1. *mySparkApp'ı*yayınlamak için aşağıdaki komutları çalıştırın:

   **Windows'da:**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **Linux üzerinde:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. HdInsight kümenize kolayca yükleyebilmeniz için yayınlanmış uygulama dosyalarınızı fermuarlamak için aşağıdaki görevleri yapın.

   **Windows'da:**

   *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*adresinden ulaş. Ardından, **Yayımla** klasörüne sağ tıklayın ve **> sıkıştırılmış (sıkıştırılmış) klasöre gönder'i**seçin. Yeni **klasörpublish.zip**adı .

   **Linux'ta aşağıdaki komutu çalıştırın:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Dosyaları Azure'a yükleme

Ardından, kümenizin depolama alanı için seçtiğiniz blob kapsayıcısına aşağıdaki beş dosyayı yüklemek için Azure Depolama Gezgini'ni kullanırsınız:

* Microsoft.Spark.Worker
* install-worker.sh
* publish.zip
* microsoft-kıvılcım-2.3.x-0.3.0.jar
* input.txt.

1. Azure Depolama Gezgini'ni açın ve sol menüden depolama hesabınıza gidin. Depolama hesabınızdaki **Blob Containers** altında kümeniz için blob konteynerine kadar inin.

2. *Microsoft.Spark.Worker,* yazdığınız kullanıcı tanımlı işlevler (UDF' ler) gibi Apache Spark'ın uygulamanızı yürütmesine yardımcı olur. [Microsoft.Spark.Worker'ı](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)karşıdan yükleyin. Ardından, çalışanı yüklemek için Azure Depolama Gezgini'nde **Yükle'yi** seçin.

   ![Dosyaları Azure Depolama Gezgini'ne yükleme](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *install-worker.sh,* Apache Spark bağımlı dosyaları için .NET'i kümenizin düğümlerine kopyalamanızı sağlayan bir komut dosyasıdır.

   Yerel bilgisayarınız **install-worker.sh** adlı yeni bir dosya oluşturun ve GitHub'da bulunan [install-worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın. Ardından, *blob* kabına install-worker.sh yükleyin.

4. Kümenizin, uygulamanızın yayınlanmış dosyalarını içeren publish.zip dosyasına ihtiyacı vardır. Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**adresine gidin ve **publish.zip'i**bulun. Sonra blob konteyner *publish.zip* yükleyin.

5. Kümenizin bir kavanoz dosyasına paketlenmiş uygulama koduna ihtiyacı vardır. Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, ve **microsoft-spark-2.3.x-0.3.0.jar.** Sonra, damla konteyner için kavanoz dosyası yükleyin.

   Birden fazla .jar dosyası olabilir (2.3.x ve Kıvılcım'ın 2.4.x sürümleri için). Küme oluşturma sırasında seçtiğiniz Kıvılcım sürümüyle eşleşen .jar dosyasını seçmeniz gerekir. Örneğin, küme oluşturma sırasında Spark 2.3.2'yi seçtiyseniz *microsoft-spark-2.3.x-0.3.0.jar'ı* seçin.

6. Kümenizin uygulamanıza girişe ihtiyacı vardır. **mySparkApp** dizininize gidin ve **input.txt'yi**bulun. Giriş dosyanızı blob kapsayıcınızdaki **kullanıcı/sshuser** dizinine yükleyin. SSh aracılığıyla kümenize bağlanabileceksiniz ve bu klasör kümenizin girişini aradığı yerdir. *Input.txt* dosyası, belirli bir dizine yüklenen tek dosyadır.

## <a name="run-the-hdinsight-script-action"></a>HDInsight komut dosyası eylemini çalıştırma

Kümeniz çalıştığında ve dosyalarınızı Azure'a yükledikten sonra, kümedeki **install-worker.sh** komut dosyasını çalıştırMış sınız.

1. Azure portalında HDInsight Spark kümenize gidin ve ardından **Komut Dosyası eylemlerini**seçin.

2. Select **+ Yeni gönder** ve aşağıdaki değerleri sağlayın:

   |Özellik  |Açıklama  |
   |---------|---------|
   | Komut dosyası türü |Özel|
   | Adı | İşçi Yükle|
   | Bash script URI |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Bu URI'yi onaylamak için Azure Depolama Gezgini'ndeki install-worker.sh sağ tıklayın ve Özellikler'i seçin. |
   | Düğüm türü(ler)| Işçi|
   | Parametreler | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/yerel/bin

3. Komut dosyanızı göndermek için **Oluştur'u** seçin.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. Azure portalında HDInsight Spark kümenize gidin ve ardından **SSH + Cluster oturum açma'yı**seçin.

2. Ssh giriş bilgilerini kopyalayın ve girişi bir terminale yapıştırın. Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın. Ubuntu ve Spark'a hoş geldin mesajları görmelisin.

3. UYGULAMANIZI HDInsight kümenizde çalıştırmak için **kıvılcım gönder** komutunu kullanın. Örnek komut dosyasındaki **mycontainer** ve **mystorage account'u** blob kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirmeyi unutmayın.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Uygulamanız çalıştığında, konsola yazılan yerel çalıştırmaya başlarken aynı sözcük sayısı tablosunu görürsünüz. Tebrikler, bulutta Apache Spark uygulaması için ilk .NET'inizi çalıştırdınız!

## <a name="clean-up-resources"></a>Kaynakları temizleme

HDInsight verilerinizi Azure Depolama'ya kaydeder, böylece kullanılmadığı bir kümeyi güvenle silebilirsiniz. Ayrıca, kullanılmıyorken dahi HDInsight kümesi için sizden ücret kesilir. Küme ücretleri depolama ücretlerinin birkaç katı olduğundan, kullanılmadığında kümelerin silinmesi mantıklı olandır.

Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz. Kaynak grubunu silerek hem HDInsight Spark kümesini hem de varsayılan depolama hesabını silersiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, .NET for Apache Spark uygulamanızı Azure HDInsight'a dağıttınız. HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight Belgelerine devam edin.

> [!div class="nextstepaction"]
> [Azure HDInsight Belgeleri](https://docs.microsoft.com/azure/hdinsight/)
