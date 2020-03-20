---
title: Windows'da Apache Spark uygulaması için bir .NET hata ayıklama
description: Windows'da Apache Spark uygulaması için .NET'inizi nasıl hata ayıklamanız gerektiğini öğrenin.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185803"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Apache Spark uygulaması için bir .NET hata ayıklama

Bu nasıl yapılsa, Windows'taki Apache Spark uygulaması için .NET'inizi hata ayıklamak için adımlar sağlar.

## <a name="debug-your-application"></a>Uygulamanızda hata ayıklama

Yeni bir komut istemi penceresi açın ve aşağıdaki komutu çalıştırın:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Komutu çalıştırdığınızda, aşağıdaki çıktıyı görürsünüz:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

Hata ayıklama modunda, DotnetRunner .NET uygulamasını başlatmaz, ancak .NET uygulamasını başlatmanızı bekler. Bu komut istemi penceresini açık bırakın ve .NET uygulamanızı C# hata ayıklama yoluyla başlatın ve uygulamanızı hata ayıkla. .NET uygulamanızı hata ayıklamak için bir C# hata[ayıklayıcı (Windows/macOS için Visual Studio Debugger](https://visualstudio.microsoft.com/vs/) veya [Visual Studio Code'da C# Debugger Uzantısı)](https://code.visualstudio.com/Docs/editor/debugging)ile başlatın.

## <a name="debug-a-user-defined-function-udf"></a>Kullanıcı tanımlı işlevin hata ayıklama (UDF)

> [!NOTE]
> Kullanıcı tanımlı işlevler yalnızca Visual Studio Debugger ile Windows'da desteklenir.

Çalıştırmadan `spark-submit`önce, aşağıdaki ortam değişkenini ayarlayın:

```bat
set DOTNET_WORKER_DEBUG=1
```

Spark uygulamanızı çalıştırdığınızda, bir `Choose Just-In-Time Debugger` pencere açılır. Visual Studio hata ayıklama seçin.

Hata ayıklama [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)aşağıdaki konumda kırılır:

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Hata ayıklamayapmayı planladığınız UDF'yi içeren *.cs* dosyasına gidin ve [bir kesme noktası ayarlayın.](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019) İşçi udf `The breakpoint will not currently be hit` içeren derlemeyi henüz yüklemediğinden, kesme noktası der ki.

Uygulamanızı devam etmek için vurmak `F5` ve kesme noktası sonunda vurulur.

> [!NOTE]
> Her görev için Tam Zamanında Hata Ayıklama penceresi açılır. Aşırı açılır pencerelerden kaçınmak için, çalıştırıcı ların sayısını düşük bir sayıya ayarlayın. Örneğin, tek bir hata ayıklama örneği başlatan görev sayısını 1 olarak ayarlamak için kıvılcım gönderme için **--ana yerel[1]** seçeneğini kullanabilirsiniz.

## <a name="debug-scala-code"></a>Hata Ayıklama Scala kodu

Scala yan kodunu`DotnetRunner`(, , `DotnetBackendHandler`vb.) hata ayıklamanız gerekiyorsa, aşağıdaki komutu kullanabilir ve [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme hata ayıklama ekleyebilirsiniz:

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Komutu çalıştırdıktan sonra, [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklama takın.

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile başlayın](../tutorials/get-started.md)
* [Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma](../tutorials/hdinsight-deployment.md)
* [Apache Spark uygulaması için Bir .NET'i Databricks'e dağıtma](../tutorials/databricks-deployment.md)
* [Amazon EMR Spark'a Apache Spark uygulaması için bir .NET dağıtın](../tutorials/amazon-emr-spark-deployment.md)
