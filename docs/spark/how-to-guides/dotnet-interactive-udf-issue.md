---
title: Apache Spark etkileşimli ortamlar için .NET 'te UDF 'Leri yazın ve çağırın.
description: Apache Spark etkileşimli kabuklar için .NET 'te UDF 'Leri yazmayı ve çağırmayı öğrenin.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c29c3a9f6269a342d1051d6d979a4e3adb42da02
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875557"
---
# <a name="write-and-call-udfs-in-net-for-apache-spark-interactive-environments"></a>Apache Spark etkileşimli ortamlar için .NET 'te UDF 'Leri yazın ve çağırın

Bu makalede, bir .NET Apache Spark etkileşimli ortamda Kullanıcı tanımlı işlevlerin (UDF) nasıl kullanılacağını öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

1. [.Net etkileşimli](https://github.com/dotnet/interactive) 'i yükler
2. [Jupyıter Laboratuvarı](https://jupyter.org/) 'nı yükler

## <a name="net-for-apache-spark-interactive-experience"></a>Apache Spark etkileşimli deneyim için .NET

[.Net Apache Spark](https://github.com/dotnet/spark) , Spark içinde etkileşimli deneyim için .NET desteği sağlamak üzere [.net etkileşimli](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) kullanır. Jupi Not defterleri ile .NET etkileşimli denemek üzere ortamı ayarlamayı anlamak için bkz. [.net etkileşimli deposu](https://github.com/dotnet/interactive).

Ayrıca, UDF 'Leri ne olduğunu ve Apache Spark için .NET ' te nasıl serileştirildiğini anlamak için [Apache Spark .net 'TEKI UDF serileştirme ile ilgili bu makaleye](udf-guide.md) gitmeniz önerilir.
Bu kılavuzda, etkileşimli bir deneyimde UDF 'Leri nasıl kullanacağınızı göstermek için Jupyıter Not defterleri kullanılmaktadır.

## <a name="define-a-udf-in-net-interactive"></a>.NET etkileşimli 'da UDF tanımlama

Etkileşimli deneyimde bir hücre, bir [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)yinelemesinin parçası olarak gönderilen kod parçacığı olarak düşünülebilir. Örneğin, şu anlama geldiğini anlamak için aşağıdaki not defterine göz atın:

![Jupyter Notebook hücreleri](./media/dotnet-interactive/dotnet-interactive-cells.png)

Kırmızı ok tarafından işaretlenen blokların her biri, bir hücredir veya kodun Spark 'a gönderilmesi. Artık Kullanıcı tanımlı özel bir nesneye başvuran bir UDF tanımlarken, UDF 'nin başvurduğu nesnenin tanımlandığı hücrede tanımlanması gerekir. Örnek olarak şöyle göründüğünü inceleyelim:

![Çalışma UDF](./media/dotnet-interactive/working-udf.png)

## <a name="call-a-udf-on-a-dataframe"></a>DataFrame üzerinde UDF çağrısı yapın

Önceden tanımlanmış bir UDF 'yi bir üzerinde çağırırken, bir `DataFrame` Önceki örnekte görünebilmesi için, daha önce gönderilen bir HÜCREDE UDF 'nin tanımlandığından emin olmak önemlidir.

Şimdi UDF 'yi, tanımlandığı hücrede çağırdığımızda ne olacağını görelim.

![UDF çağrısı başarısız](./media/dotnet-interactive/udf_fails.png)

Yukarıdaki vurgulanan hata, UDF derlemelerinin bir veri çerçevesinde çağrılabilmesi için önce derlenmesi ve çalışanlara sevk edilmemesinden kaynaklanır.

Bunlar, Apache Spark etkileşimli deneyimle ( [Azure SYNAPSE Not defterleri](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks)gibi), .net 'Te UDF 'leri uygularken göz önünde bulundurmanız gereken birkaç önemli şey vardır.

## <a name="faqs"></a>SSS

1. **UDF 'im özel kullanıcı tanımlı bir nesneye neden bir hata oluşturur `Type Submission#_ is not marked as serializable` ?**
    .NET etkileşimli, gönderilen her hücreyi benzersiz bir şekilde tanımlamak için bu hücrelerden her birini hücre gönderim numarasının bir sarmalayıcı sınıfıyla sarmalar. Artık [Bu kılavuzda](udf-guide.md)ayrıntılı olarak açıklandığı gibi, özel bir nesneye başvuran bir UDF 'nin hedefi, .net etkileşimli olması durumunda özel nesnenin tanımlandığı hücrenin sarmalayıcı sınıfı tarafından sarmalanması durumunda serileştirme için de oluşturulur.
    Şimdi bunu, not defterinde UDF tanımımızı nasıl etkilediğini görelim:

    ![UDF serileştirme hatası](./media/dotnet-interactive/udf-serialization-error.png)

    Bu durumda görünebileceği gibi `udf2_fails` , türün `Submission#7` seri hale getirilebilir olarak işaretlenmediğini belirten hata iletisini görüyoruz. bunun nedeni, .net etkileşimli 'in, bir hücrede tanımlanan her nesneyi, çalışma alanında `Submission#` oluşturulan ve bu nedenle olarak işaretlenmeyen sınıfıyla sardığı durumdur `Serializable` .

    Bu nedenle, **özel bir nesneye başvuran BIR UDF 'nin bu nesneyle aynı hücrede tanımlanması gerekir**.

2. **Neden yayınlama değişkenleri .NET etkileşimli ile çalışır?**
    Daha önce açıklanan nedenlerden dolayı yayın değişkenleri .NET etkileşimli ile çalışmaz. Yayın değişkenlerinin ne olduğunu ve bunların nasıl kullanılacağını daha ayrıntılı bir şekilde anlamak için [yayın değişkenlerinde bu kılavuzdan](broadcast-guide.md) geçmek iyi bir fikirdir. Yayın değişkenlerinin etkileşimli senaryolarla çalışmamasının nedeni, .NET etkileşimli 'nin bir hücrede tanımlanan her nesneyi hücre gönderim sınıfıyla birlikte ekleme, bu nedenle seri hale getirilebilir olarak işaretlenmemiş, ancak daha önce gösterildiği gibi aynı özel durumla başarısız olduğu anlamına gelir.
    Aşağıdaki örnekte biraz daha ayrıntılı bilgi verelim:

    ![Yayın değişkenleri başarısız](./media/dotnet-interactive/broadcast-fails.png)

    Önceki bölümlerde önerildiği gibi, aynı hücrede hem UDF 'yi hem de başvurduğu nesneyi (Bu durumda yayın değişkeni) tanımlayacağız, ancak yine de `SerializationException` `Microsoft.Spark.Sql.Session` seri hale getirilebilir olarak işaretlenmeyen hata şikayetinizi görtik. Bunun nedeni, derleyicinin yayın değişken nesnesini serileştirmek için yaptığı bir `bv` , onun adını, [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) `spark` seri hale getirilebilir olarak işaretlenmesi gereken nesne ile sonuna kadar bulur. Bu hücre gönderimi, derlenmiş derleme derlemesinde göz önünde bulundurularak daha kolay bir şekilde gösterilmiştir:

    ![Ayrıştırılmış derleme kodu](./media/dotnet-interactive/decompiledAssembly.png)

    Sınıfı olarak işaretliyoruz, bu özelliği işe sunabiliyoruz, [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) `[Serializable]` ancak kullanıcıya bir mini oturum nesnesini seri hale getirme yeteneği vermek istemediğimiz için bu ideal bir çözüm değildir. Bu bilinen bir [sorundur](https://github.com/dotnet/spark/issues/619) ve gelecek sürümlerde çözümlenir.
