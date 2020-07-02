---
title: Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma
description: HDInsight için bir .NET Apache Spark uygulamasının nasıl dağıtılacağını öğrenin.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e6b2fdd1818250c47ce6cb64439ecab58ae99ad8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617645"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Öğretici: Azure HDInsight 'a Apache Spark uygulaması için .NET dağıtma

Bu öğreticide, Azure HDInsight kümesi aracılığıyla Apache Spark için .NET uygulamanızı buluta nasıl dağıtacağınız öğretilir. HDInsight 'ta Spark kümeleri Azure depolama ve Azure Data Lake Storage uyumlu olduğundan, HDInsight, Azure 'da Spark kümesi oluşturmayı ve yapılandırmayı kolaylaştırır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Azure Depolama Gezgini kullanarak depolama hesaplarınıza erişin.
> * Azure HDInsight kümesi oluşturma.
> * Apache Spark için .NET uygulamanızı yayımlayın.
> * HDInsight betik eylemi oluşturun ve çalıştırın.
> * HDInsight kümesinde Apache Spark uygulaması için bir .NET çalıştırın.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Ön koşullar

Başlamadan önce, aşağıdaki görevleri yapın:

* Azure aboneliğiniz yoksa [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/)oluşturun.
* [Azure Portal](https://portal.azure.com/) oturum açın.
* [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)veya [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) bilgisayarınıza Azure Depolama Gezgini ' yi yükler.
* [Apache Spark için .net ' i doldurun-10 dakikalık öğreticide kullanmaya başlayın](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .

## <a name="access-your-storage-accounts"></a>Depolama hesaplarınıza erişin

1. Azure Depolama Gezgini açın.

2. Sol menüden **Hesap Ekle** ' yi seçin ve Azure hesabınızda oturum açın.

    ![Depolama Gezgini Azure hesabında oturum açın](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Oturum açtıktan sonra, sahip olduğunuz tüm depolama hesaplarını ve depolama hesaplarınıza yüklediğiniz kaynakları görmeniz gerekir.

## <a name="create-an-hdinsight-cluster"></a>HDInsight kümesi oluşturma

> [!IMPORTANT]
> HDInsight kümelerinin faturalandırılması, kullanmadığınız olsalar dahi, dakikada eşit olarak dağıtılır. Kullanmayı bitirdikten sonra kümenizi sildiğinizden emin olun. Daha fazla bilgi için Bu öğreticinin [Temizleme kaynakları](#clean-up-resources) bölümüne bakın.

1. [Azure Portal](https://portal.azure.com)ziyaret edin.

2. **+ Kaynak oluştur**’u seçin. Ardından **analiz** kategorisinden **HDInsight** ' ı seçin.

    ![Azure portal HDInsight kaynağı oluşturma](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. **Temel Bilgiler** bölümünde aşağıdaki değerleri sağlayın:

    |Özellik  |Açıklama  |
    |---------|---------|
    |Abonelik  | Açılan listeden, etkin Azure aboneliklerinizden birini seçin. |
    |Kaynak grubu | Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin. Kaynak grubu, bir Azure çözümüne ilişkin kaynakları tutan bir kapsayıcıdır. |
    |Küme adı | HDInsight Spark kümenize bir ad verin.|
    |Konum   | Kaynak grubu için bir konum seçin. Şablon hem kümeyi oluşturmak için hem de varsayılan küme depolaması için bu konumu kullanır. |
    |Küme türü| Küme türü olarak **Spark** ' ı seçin.|
    |Küme sürümü|Bu alan, küme türü seçildikten sonra varsayılan sürüm ile oto doldurulur. Spark 'ın 2,3 veya 2,4 sürümünü seçin.|
    |Küme oturum açma kullanıcı adı| Küme oturum açma kullanıcı adını girin.  Varsayılan ad, *admin* şeklindedir. |
    |Küme oturum açma parolası| Herhangi bir oturum açma parolası girin. |
    |Secure Shell (SSH) kullanıcı adı| SSH kullanıcı adını girin. Varsayılan olarak bu hesap, *Küme Oturum Açma kullanıcı adı* hesabıyla aynı parolayı paylaşır. |

4. Ileri ' yi seçin: **depolama sayfasına devam** etmek için **depolama >>** . **Depolama** bölümünde aşağıdaki değerleri sağlayın:

    |Özellik  |Açıklama  |
    |---------|---------|
    |Birincil depolama türü|Varsayılan **Azure Storage**değerini kullanın.|
    |Seçim yöntemi|Varsayılan değer **listesinden Seç ' i**kullanın.|
    |Birincil depolama hesabı|Aboneliğinizi ve bu abonelik içindeki etkin depolama hesaplarınızdan birini seçin.|
    |Kapsayıcı|Bu kapsayıcı, depolama hesabınızda, kümenizin uygulamanızı bulutta çalıştırmak için dosya aradığı belirli bir blob kapsayıcısıdır. Kullanılabilir herhangi bir ad verebilirsiniz.|

5. **Gözden geçir + oluştur**altında **Oluştur**' u seçin. Kümenin oluşturulması yaklaşık 20 dakika sürer. Sonraki adıma devam edebilmeniz için önce kümenin oluşturulması gerekir.

## <a name="publish-your-app"></a>Uygulamanızı yayımlama

Daha sonra, [Apache Spark için .net](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) sürümünde oluşturulan *mySparkApp* 'yi yayımlarsınız ve bu, Spark kümesine uygulamanızı çalıştırmak için gereken tüm dosyalara erişim sağlayan 10 dakikalık öğreticide çalışmaya başlayın.

1. *MySparkApp*yayımlamak için aşağıdaki komutları çalıştırın:

   **Windows 'da:**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **Linux 'ta:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Bunları HDInsight kümenize kolayca yükleyebilmeniz için, yayımlanmış uygulama dosyalarınızı Zip halinde aşağıdaki görevleri yapın.

   **Windows 'da:**

   *MySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*dizinine gidin. Ardından, **Yayımla** klasörüne sağ tıklayıp **> sıkıştırılmış (daraltılmış) klasöre gönder**' i seçin. Yeni klasörü **publish.zip**olarak adlandırın.

   **Linux 'ta aşağıdaki komutu çalıştırın:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Azure 'a dosya yükleme

Ardından, aşağıdaki beş dosyayı kümenizin depolaması için seçtiğiniz blob kapsayıcısına yüklemek için Azure Depolama Gezgini kullanırsınız:

* Microsoft. spark. Worker
* install-worker.sh
* publish.zip
* Microsoft-Spark-2.3. x-0.3.0. jar
* input.txt.

1. Azure Depolama Gezgini açın ve sol menüden depolama hesabınıza gidin. Depolama hesabınızdaki **BLOB kapsayıcıları** altındaki kümeniz için blob kapsayıcısının ayrıntılarına gidin.

2. *Microsoft. spark. Worker* , yazdığınız kullanıcı tanımlı Işlevler (UDF 'ler) gibi uygulamanızı Apache Spark yürütmenize yardımcı olur. [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)öğesini indirin. Ardından, çalışanı karşıya yüklemek için Azure Depolama Gezgini **karşıya yükle** ' yi seçin.

   ![Dosyaları Azure Depolama Gezgini karşıya yükleme](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *İnstall-Worker.sh* , Apache Spark bağımlı dosyaları için .net ' i kümenizin düğümlerine kopyalamanızı sağlayan bir betiktir.

   Yerel bilgisayarınızı **install-Worker.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [install-Worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın. Sonra, blob kapsayıcınıza *install-Worker.sh* yükleyin.

4. Kümeniz, uygulamanızın yayımlanan dosyalarını içeren publish.zip dosyasına ihtiyaç duyuyor. Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**ve **publish.zip**bulun. Sonra *publish.zip* blob kapsayıcınıza yükleyin.

5. Kümeniz, bir jar dosyasına paketlenmiş uygulama koduna ihtiyaç duyuyor. Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**ve **Microsoft-Spark-2.3. x-0.3.0. jar**konumunu bulun. Ardından, JAR dosyasını blob kapsayıcınıza yükleyin.

   Birden çok. jar dosyası olabilir (örneğin, 2.3. x ve 2,4. x Spark sürümü için). Küme oluşturma sırasında seçtiğiniz Spark sürümü ile eşleşen. jar dosyasını seçmeniz gerekir. Örneğin, küme oluşturma sırasında Spark 2.3.2 ' yı seçtiyseniz *Microsoft-Spark-2.3. x-0.3.0. jar* öğesini seçin.

6. Kümenizin uygulamanıza giriş yapması gerekiyor. **MySparkApp** dizininize gidin ve **input.txt**bulun. Giriş dosyanızı blob kabınızda **Kullanıcı/sshuser** dizinine yükleyin. SSH aracılığıyla kümenize bağlanırsınız ve bu klasör, kümenizin girişi için bakacağı yerdir. *input.txt* dosyası, belirli bir dizine yüklenen tek dosyadır.

## <a name="run-the-hdinsight-script-action"></a>HDInsight betiği eylemini Çalıştır

Kümeniz çalışır olduktan sonra dosyalarınızı Azure 'a yükledikten sonra kümede **install-Worker.sh** betiğini çalıştırırsınız.

1. Azure portal HDInsight Spark kümenize gidin ve **betik eylemleri**' ni seçin.

2. **+ Yeni Gönder** ' i seçin ve aşağıdaki değerleri sağlayın:

   |Özellik  |Açıklama  |
   |---------|---------|
   | Betik türü |Özel|
   | Name | Çalışanı yükler|
   | Bash betiği URI 'SI |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> Bu URI 'yi onaylamak için Azure Depolama Gezgini 'de install-worker.sh öğesine sağ tıklayın ve Özellikler ' i seçin. |
   | Düğüm türleri| Indan|
   | Parametreler | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. Komut dosyanızı göndermek için **Oluştur** ' u seçin.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. Azure portal HDInsight Spark kümenize gidin ve ardından **SSH + küme oturumu aç**' ı seçin.

2. SSH oturum açma bilgilerini kopyalayın ve oturumu bir terminale yapıştırın. Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın. Sizi Ubuntu ve Spark 'a yönlendiren iletiler görmeniz gerekir.

3. Uygulamanızı HDInsight kümenizde çalıştırmak için **Spark-gönder** komutunu kullanın. Örnek betikteki **myContainer** ve **mystorageaccount** ' ın blob Kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirilmesini unutmayın.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Uygulamanız çalıştığında, Başlarken yerel çalıştırmasından konsola yazılan aynı sözcük sayısı tablosunu görürsünüz. Tebrikler, ilk .NET Apache Spark uygulamanızı bulutta çalıştırdık!

## <a name="clean-up-resources"></a>Kaynakları temizleme

HDInsight, verileri Azure Storage 'a kaydeder, bu sayede bir kümeyi kullanımda olmadığında güvenle silebilirsiniz. Ayrıca, kullanılmıyorken dahi HDInsight kümesi için sizden ücret kesilir. Küme ücretleri depolama ücretlerinin birkaç katı olduğundan, kullanılmadığında kümelerin silinmesi mantıklı olandır.

Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz. Kaynak grubunu silerek hem HDInsight Spark kümesini hem de varsayılan depolama hesabını silersiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, .NET Apache Spark uygulamanızı Azure HDInsight 'a dağıttınız. HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight belgelerine geçin.

> [!div class="nextstepaction"]
> [Azure HDInsight Belgeleri](https://docs.microsoft.com/azure/hdinsight/)
