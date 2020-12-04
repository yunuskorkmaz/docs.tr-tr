---
title: Jupyter Notebook'u kullanma
titleSuffix: .NET for Apache Spark
description: Jupyter Notebook, Jupyıter Laboratuvarı veya Visual Studio Code gibi etkileşimli ortamlarda Apache Spark için .NET kullanın (VS Code)
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: cf19b4e4b7a7b9033fb97b2b2736ab0383c11f93
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96598939"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a>Jupyıter not defterlerinde Apache Spark için .NET kullanın

Bu makalede, .net etkileşimli ile Jupyter Notebook ve Visual Studio Code (VS Code) Apache Spark işlerini etkileşimli olarak nasıl çalıştıracağınızı öğreneceksiniz.

## <a name="about-jupyter"></a>Jupyıter hakkında

[Jupyıter](https://jupyter.org/) , kullanıcıların uygulamaları etkileşimli olarak prototip ve geliştirmesini sağlayan bir yol sağlayan açık kaynaklı, platformlar arası bir bilgi işlem ortamıdır. Jupyter Notebook, Jupyıter Laboratuvarı ve VS Code gibi çok çeşitli arabirimler aracılığıyla Jupyıter ile etkileşim kurabilirsiniz.

.NET Core küresel aracı olan .net, .net [etkileşimli](https://github.com/dotnet/interactive)bağlamında, Jupyter Notebook gibi etkileşimli bilgi işlem ortamlarında .NET kodu (C#/f #) yazmak için bir çekirdek sağlar.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3,1 SDK](../../core/install/index.yml)
- [Apache Spark](https://spark.apache.org/downloads.html)
- [Apache Spark .NET Worker](https://github.com/dotnet/spark/releases)

Apache Spark ortamınızı .NET için ayarlama hakkında daha fazla bilgi için bkz. Başlangıç [öğreticisi](../tutorials/get-started.md) .

## <a name="prepare-environment"></a>Ortamı hazırlama

Jupi Not defterleri ile çalışmak için iki şey olması gerekir.

1. [.Net etkileşimli küresel .NET aracını](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md) yükler
1. `Microsoft.Spark`NuGet paketini indirin.
    1. [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketi sayfasına gidin.

        > [!IMPORTANT]
        > Varsayılan olarak, paketin en son sürümü indirilir. **İndirdiğinizden emin olun Apache Spark .NET çalışanınız ile aynı.**

    1. **Bilgi** bölmesinde, paketin en son sürümünü indirmek Için **paketi indir** ' i seçin. Paketin adı  *Microsoft. Spark ile benzerdir. [ Paket-sürümü]. nupkg*.
    1. İndirilen paketi sıkıştırmayı açın. Sıkıştırılmış olmayan dizin, *jar dosyaları dışındaki* adlı bir alt dizin içermelidir. Daha sonraki bir zamanda kullanıldığından yola göz atın.

## <a name="start-net-for-apache-spark"></a>Apache Spark için .NET 'i başlatın

Hata ayıklama modunda Apache Spark için .NET 'i başlatmak üzere aşağıdaki komutu çalıştırın. Bu `spark-submit` komut bir işlem başlatır ve bir [mini oturum](xref:Microsoft.Spark.Sql.SparkSession)bağlantısı bekler. `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`Kullandığınız Apache Spark ilgili .NET sürümü için yolunu sağladığınızdan emin olun.

**Ubuntu**

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

**Windows**

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a>Not defteri oluşturma

Jupyıter ile etkileşim kurmak için farklı arabirimler kullanabilirsiniz. Tarayıcı tabanlı bir arabirim için Jupyıter not defterlerini veya Jupyıter Laboratuvarı kullanın. Yerel bir düzenleyici deneyimi için VS Code kullanın.

### <a name="jupyter-notebooks--jupyter-lab"></a>Jupi Notebook & Jupyıter Laboratuvarı

1. Başka bir komut isteminde, aşağıdaki komutlardan birini kullanarak Jupyter Notebook veya Jupyter Laboratuvarı başlatın:

    **Jupyter Notebook**

    ```bash
    jupyter notebook
    ```

    **Jupyıter Laboratuvarı**

    ```bash
    jupyter lab
    ```

    Bu komutlar Jupyter Notebook veya Jupyıter laboratuvar arabirimiyle bir tarayıcı penceresi başlatır.

1. Tarayıcıda yeni bir not defteri oluşturun.

    **Jupyter Notebook**

    **Yeni > .net (C#)** veya **Yeni > .NET seçin (F #)**

    **Jupyıter Laboratuvarı**

    Başlatıcı penceresinde **.net (C#)** veya **.NET seçin (F #)**

### <a name="visual-studio-code-preview"></a>Visual Studio Code (Önizleme)

> [!IMPORTANT]
> Jupyter not defterlerini VS Code kullanmak için şunu yüklemelisiniz:
>
>- [VS Code Insiders](https://code.visualstudio.com/insiders/)
>- [.NET etkileşimli not defterleri uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. VS Code’u açın.
1. Komut paleti **görünümünü > komut paleti**' ni açın.

    Komut paleti göründüğünde, yeni bir .NET etkileşimli not defteri oluşturmak için aşağıdaki komutu girin:

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    Alternatif olarak, var olan bir .NET etkileşimli not defterini *. ipynb* uzantısıyla açmak istiyorsanız aşağıdaki komutu kullanın:

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a>Spark oturumu başlatma

1. Not Defteri açıldığında, `Microsoft.Spark` NuGet paketini yükler. Yüklediğiniz sürümün .NET Worker ile aynı olduğundan emin olun.

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. Aşağıdaki using ifadesini not defterine ekleyin.

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. [Mini oturum oturumunuzu](xref:Microsoft.Spark.Sql.SparkSession)başlatın.

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

Not defteri aşağıdaki görüntüde gösterilene benzer görünmelidir. Bu örnek VS Code kullanır, ancak Jupyter Notebook ve Jupyıter Laboratuvarı aynı şekilde görünmelidir.

> [!div class="mx-imgBorder"]
![Apache Spark Jupyter Notebook için .NET VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)

## <a name="next-steps"></a>Sonraki Adımlar

- [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
- [Apache Spark ve ML.NET için .NET kullanarak yaklaşımı tahmin edin](../tutorials/ml-sentiment-analysis.md)
- .NET etkileşimli hakkında daha fazla bilgi için bkz. [.net etkileşimli belgeleri](https://github.com/dotnet/interactive/blob/main/docs/README.md).
