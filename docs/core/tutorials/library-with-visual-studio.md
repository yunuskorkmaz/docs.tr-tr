---
title: Visual Studio 'da .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio kullanarak C# veya Visual Basic yazılmış .NET Standard sınıf kitaplığı oluşturmayı öğrenin
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714015"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Visual Studio 'da .NET Standard kitaplığı oluşturma

Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir. Sınıf kitaplığınızı bitirdiğinizde, bunu üçüncü taraf bir bileşen olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.

> [!NOTE]
> .NET Standard sürümlerinin ve destekledikleri platformların listesi için bkz. [.NET Standard](../../standard/net-standard.md).

Bu konu başlığında, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız. Bunu, <xref:System.String> sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulayacaksınız.

## <a name="create-a-visual-studio-solution"></a>Visual Studio çözümü oluşturma

' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın. Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür. Öğretici serisiyle devam ederseniz, aynı çözüme ek ve ilgili projeler ekleyeceksiniz.

Boş çözümü oluşturmak için:

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin. **Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin. Ardından **Oluştur**' u seçin.

> [!TIP]
> Ayrıca, bu adımı atlayabilir ve bir sonraki adımda projeyi oluştururken Visual Studio 'nun sizin için çözümü oluşturmasına izin verebilirsiniz. **Yeni projenizde yapılandırma** sayfasında çözüm seçeneklerini bulun.

## <a name="create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Çözüme "StringLibrary" adlı yeni C# bir .NET Standard sınıf kitaplığı projesi ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın. Dil **C#** listesinden seçim yapın ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın. Ardından **Oluştur**' u seçin.

1. Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun. **Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin. **Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   `UtilityLibraries.StringLibrary`sınıf kitaplığı, `StartsWithUpper`adlı bir yöntemi içerir. Bu yöntem, geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir <xref:System.Boolean> değeri döndürür. Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> yöntemi, bir karakter büyük harfle `true` döndürür.

1. Menü çubuğunda **derleme** > **Build Solution**' ı seçin.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Çözüme "StringLibrary" adlı yeni bir Visual Basic .NET Standard sınıf kitaplığı projesi ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın. Dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın. Ardından **Oluştur**' u seçin.

1. Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun. **Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin. **Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

1. **Özellikler** iletişim kutusunda, **kök ad alanı** metin kutusundaki metni temizleyin. Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur. Bu öğreticide, kod dosyasında [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğünü kullanarak en üst düzey bir ad alanı tanımlarsınız.

1. Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   `UtilityLibraries.StringLibrary`sınıf kitaplığı, `StartsWithUpper`adlı bir yöntemi içerir. Bu yöntem, geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir <xref:System.Boolean> değeri döndürür. Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> yöntemi, bir karakter büyük harfle `true` döndürür.

1. Menü çubuğunda **derleme** > **Build Solution**' ı seçin.

---

   Projenin hatasız derlenmesi gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Kitaplığı başarıyla derlediniz. Yöntemlerinden herhangi birini çağırmadığınız için, beklendiği gibi çalışıp çalışmadığını bilemezsiniz. Kitaplığınızı geliştirmedeki bir sonraki adım, test etmek için kullanılır.

> [!div class="nextstepaction"]
> [Birim testi projesi oluşturma](testing-library-with-visual-studio.md)
