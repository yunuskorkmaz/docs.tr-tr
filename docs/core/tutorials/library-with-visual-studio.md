---
title: Visual Studio'da .NET Standart sınıf kitaplığı oluşturma
description: Visual Studio'u kullanarak C# veya Visual Basic ile yazılmış bir .NET Standart sınıf kitaplığı oluşturmayı öğrenin
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714015"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Visual Studio'da bir .NET Standart kitaplığı oluşturun

*Sınıf kitaplığı,* uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. .NET Standart 2.0'ı hedefleyen bir sınıf kitaplığı, kitaplığınızın .NET Standard'ın bu sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılmasını sağlar. Sınıf kitaplığınızı bitirdiğinizde, onu üçüncü taraf bileşeni olarak mı yoksa bir veya daha fazla uygulamaiçeren paketlenmiş bir bileşen olarak mı eklemek istediğinize karar verebilirsiniz.

> [!NOTE]
> .NET Standart sürümlerinin ve destekledikleri platformların listesi [için](../../standard/net-standard.md)bkz.

Bu konuda, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturursunuz. Sınıfın bir üyesiysek <xref:System.String> diye adlandırabilmeniz için bunu bir [uzantı yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygularsınız.

## <a name="create-a-visual-studio-solution"></a>Visual Studio çözümü oluşturun

Sınıf kitaplığı projesini koymak için boş bir çözüm oluşturarak başlayın. Visual Studio çözümü, bir veya daha fazla proje için bir kapsayıcı görevi görehizmet eder. Öğretici seriye devam ederseniz, aynı çözüme ek, ilgili projeler eklersiniz.

Boş çözümü oluşturmak için:

1. Visual Studio'yu açın.

2. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

3. Yeni **bir proje oluştur** sayfasında, **çözüm** arama kutusuna girin. Boş **Çözüm** şablonu'nu seçin ve sonra **İleri'yi**seçin.

   ![Visual Studio'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. Yeni **proje sayfanızı Yapılandır'da,** Proje **adı** kutusuna **ClassLibraryProjects'i** girin. Ardından **Oluştur'u**seçin.

> [!TIP]
> Ayrıca bu adımı atlayabilir ve bir sonraki adımda projeyi oluştururken Visual Studio'nun sizin için çözüm oluşturmasına izin verebilirsiniz. **Yeni proje sayfanızda Yapılandır'daki** çözüm seçeneklerini arayın.

## <a name="create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Çözüme "StringLibrary" adlı yeni bir C# .NET Standart sınıf kitaplık projesi ekleyin.

   1. **Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.

   1. Yeni **bir proje ekle** sayfasında, arama kutusuna **kitaplığı** girin. Dil listesinden **C#** seçeneğini seçin ve ardından Platform listesinden **Tüm platformları** seçin. Sınıf **Kitaplığı (.NET Standart)** şablonu seçin ve sonra **İleri'yi**seçin.

   1. Yeni **proje sayfanızı Yapılandır'da,** **Proje adı** kutusuna **StringLibrary'yi** girin. Ardından **Oluştur'u**seçin.

1. Kitaplığın .NET Standard'ın doğru sürümünü hedefaldığından emin olun. **Çözüm Gezgini'ndeki**kitaplık projesine sağ tıklayın ve ardından **Özellikler'i**seçin. **Hedef Çerçeve** metin kutusu, projenin .NET Standard 2.0'ı hedefaldığını gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Sınıf kitaplığı, `UtilityLibraries.StringLibrary`adlı `StartsWithUpper`bir yöntem içerir. Bu yöntem, <xref:System.Boolean> geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını gösteren bir değer döndürür. Unicode standardı büyük harflerkarakterleri küçük karakterlerden ayırır. Bir <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> karakter `true` büyük harfse yöntem döndürür.

1. Menü çubuğunda **Yapı** > **Çözümünü**seçin.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Çözüme "StringLibrary" adlı yeni bir Visual Basic .NET Standart sınıf kitaplık projesi ekleyin.

   1. **Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.

   1. Yeni **bir proje ekle** sayfasında, arama kutusuna **kitaplığı** girin. Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesindeki **Tüm platformları** seçin. Sınıf **Kitaplığı (.NET Standart)** şablonu seçin ve sonra **İleri'yi**seçin.

   1. Yeni **proje sayfanızı Yapılandır'da,** **Proje adı** kutusuna **StringLibrary'yi** girin. Ardından **Oluştur'u**seçin.

1. Kitaplığın .NET Standard'ın doğru sürümünü hedefaldığından emin olun. **Çözüm Gezgini'ndeki**kitaplık projesine sağ tıklayın ve ardından **Özellikler'i**seçin. **Hedef Çerçeve** metin kutusu, projenin .NET Standard 2.0'ı hedefaldığını gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

1. **Özellikler** iletişim kutusunda, Kök ad **alanı** metin kutusundaki metni temizleyin. Her proje için Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur. Bu öğreticide, kod dosyasındaki anahtar kelimeyi [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) kullanarak üst düzey bir ad alanı tanımlarsınız.

1. Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Sınıf kitaplığı, `UtilityLibraries.StringLibrary`adlı `StartsWithUpper`bir yöntem içerir. Bu yöntem, <xref:System.Boolean> geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını gösteren bir değer döndürür. Unicode standardı büyük harflerkarakterleri küçük karakterlerden ayırır. Bir <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> karakter `true` büyük harfse yöntem döndürür.

1. Menü çubuğunda **Yapı** > **Çözümünü**seçin.

---

   Proje hatasız derlemelidir.

## <a name="next-steps"></a>Sonraki adımlar

Kütüphaneyi başarıyla inşa ettin. Yöntemlerinin hiçbirini aramadığınız için beklendiği gibi çalışıp çalışmadığını bilmiyorsun. Kitaplığınızı geliştirmenin bir sonraki adımı bunu test etmektir.

> [!div class="nextstepaction"]
> [Birim testi projesi oluşturma](testing-library-with-visual-studio.md)
