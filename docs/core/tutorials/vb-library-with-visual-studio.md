---
title: Visual Studio 2017 'de Visual Basic .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio 2017 kullanarak Visual Basic yazılmış .NET Standard sınıf kitaplığı oluşturmayı öğrenin
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100862"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a>Visual Studio 2017 ' de Visual Basic ve .NET Core SDK ile .NET Standard kitaplığı oluşturma

Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen tüm .NET uygulamaları tarafından çağrılmasına izin verir. Sınıf kitaplığınızı bitirdiğinizde, bunu üçüncü taraf bir bileşen olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.

> [!NOTE]
> .NET Standard sürümlerinin ve destekledikleri platformların bir listesi için bkz. [.NET Standard](../../standard/net-standard.md).

Bu konu başlığında, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız. Bunu, <xref:System.String> sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) olarak uygulayacaksınız.

## <a name="creating-a-class-library-solution"></a>Sınıf kitaplığı çözümü oluşturma

Sınıf kitaplığı projeniz ve ilgili projeler için bir çözüm oluşturarak başlayın. Bir Visual Studio çözümü yalnızca bir veya daha fazla proje için kapsayıcı görevi görür. Çözümü oluşturmak için:

1. Visual Studio menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.

1. **Yeni proje** Iletişim kutusunda **diğer proje türleri** düğümünü genişletin ve **Visual Studio çözümleri**' ni seçin. "ClassLibraryProjects" çözümünü adlandırın ve **Tamam** düğmesini seçin.

   ![Visual Studio yeni test projesi oluştur iletişim kutusu](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

Sınıf kitaplığı projenizi oluşturun:

1. **Çözüm Gezgini**, **classlibraryprojects** çözüm dosyasına sağ tıklayın ve bağlam menüsünden **Yeni proje** > **Ekle** ' yi seçin.

1. **Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümünü genişletin ve ardından **.NET Standard** düğümünü ve ardından **sınıf kitaplığı (.NET Standard)** proje şablonunu seçin. **Ad** metin kutusuna projenin adı olarak "StringLibrary" yazın. Sınıf Kitaplığı projesini oluşturmak için **Tamam ' ı** seçin.

   ![Visual Studio yeni kitaplık projesi Ekle iletişim kutusu](./media/vb-library-with-visual-studio/create-new-library-project.png)

   Kod penceresi daha sonra Visual Studio geliştirme ortamında açılır. 
 
   ![Varsayılan sınıf kitaplığı şablon kodunu gösteren Visual Studio uygulama penceresi](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. Kitaplığın .NET Standard doğru sürümünü hedeflediğinden emin olun. **Çözüm Gezgini** penceresinde kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin. **Hedef Framework** metin kutusunda 2,0 .NET Standard hedeflendiğimiz gösterilmektedir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. Ayrıca **Özellikler** iletişim kutusunda, **kök ad alanı** metin kutusundaki metni temizleyin. Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur ve kaynak kod dosyalarında tanımlanan ad alanları bu ad alanının üstlerdir. [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğünü kullanarak en üst düzey bir ad alanı tanımlamak istiyoruz.
  
1. Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   `UtilityLibraries.StringLibrary`sınıf kitaplığı, geçerli dize örneğinin büyük bir karakterle başlayıp başlamadığını belirten bir <xref:System.Boolean> değeri döndüren `StartsWithUpper`adlı bir yöntemi içerir. Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> yöntemi, bir karakter büyük harfle `true` döndürür.

1. Menü çubuğunda **derleme** > **Build Solution**' ı seçin. Projenin hatasız derlenmesi gerekir.

   ![Yapılandırmanın başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Sonraki adım

Kitaplığı başarıyla derlediniz. Yöntemlerinden herhangi birini çağırmadığınız için, beklendiği gibi çalışıp çalışmadığını bilemezsiniz. Kitaplığınızı geliştirmedeki bir sonraki adım, bir [birim testi projesi](testing-library-with-visual-studio.md)kullanarak test kullanmaktır.
