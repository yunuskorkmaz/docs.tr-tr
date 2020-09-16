---
title: Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama
description: Windows 'da Apache Spark için .NET uygulamanızı nasıl ayıklayacağınızı öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 249b4bccbf1378d8ef8c824f39151c33fb9f875a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557157"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Apache Spark uygulama için bir .NET hatası ayıklama

Bu nasıl yapılır, Windows 'da Apache Spark için .NET uygulamanızı hata ayıklama adımlarını sağlar.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a>Uygulamanızda hata ayıklama

Yeni bir komut istemi penceresi açın ve aşağıdaki komutu çalıştırın:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Komutu çalıştırdığınızda aşağıdaki çıktıyı görürsünüz:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

Hata ayıklama modunda, DotnetRunner .NET uygulamasını başlatmaz, bunun yerine .NET uygulamasını başlatmanız için bekler. Uygulamanızda hata ayıklamak için bu komut istemi penceresini açık bırakın ve C# hata ayıklayıcısı aracılığıyla .NET uygulamanızı başlatın. Uygulamanızda hata ayıklamak için bir C# hata ayıklayıcı ([Windows/macOS Için Visual Studio hata ayıklayıcı](https://visualstudio.microsoft.com/vs/) veya [C# hata ayıklayıcı uzantısı Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) ile .NET uygulamanızı başlatın.

## <a name="debug-a-user-defined-function-udf"></a>Kullanıcı tanımlı bir işlevde hata ayıklama (UDF)

> [!NOTE]
> Kullanıcı tanımlı işlevler yalnızca Visual Studio hata ayıklayıcı ile Windows 'da desteklenir.

Çalıştırmadan önce `spark-submit` Aşağıdaki ortam değişkenini ayarlayın:

```bat
set DOTNET_WORKER_DEBUG=1
```

Spark uygulamanızı çalıştırdığınızda bir `Choose Just-In-Time Debugger` pencere açılır. Bir Visual Studio hata ayıklayıcısı seçin.

Hata ayıklayıcı [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)içinde aşağıdaki konumda kesilir:

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Hata ayıklamayı planladığınız UDF 'yi içeren *. cs* dosyasına gidin ve [bir kesme noktası ayarlayın](/visualstudio/debugger/using-breakpoints?view=vs-2019). `The breakpoint will not currently be hit`Çalışan, UDF içeren derlemeyi henüz yüklememediği için kesme noktası olacaktır.

`F5`Uygulamanıza devam etmek için isabet, sonunda kesme noktasına ulaşıldı.

> [!NOTE]
> Tam zamanında hata ayıklayıcı Seç penceresi her bir görev için açılır. Aşırı açılan pencerelerin olmaması için, yürüticilerinin sayısını düşük bir sayı olarak ayarlayın. Örneğin, tek bir hata ayıklayıcı örneği başlatan görev sayısını 1 olarak ayarlamak için Spark-Gönder için **--Master yerel [1]** seçeneğini kullanabilirsiniz.

## <a name="debug-scala-code"></a>Scala kodunda hata ayıklama

Scala tarafı kodunda ( `DotnetRunner` , `DotnetBackendHandler` , vb.) hata ayıklaması yapmanız gerekirse, aşağıdaki komutu kullanabilir ve [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklayıcı ekleyebilirsiniz:

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Komutu çalıştırdıktan sonra, [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklayıcı ekleyin.

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)
* [Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı](../tutorials/databricks-deployment.md)
* [Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma](../tutorials/amazon-emr-spark-deployment.md)
