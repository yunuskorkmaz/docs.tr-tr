---
title: Derleme bir C# Visual Studio 2017 ile .NET Standard kitaplığı
description: Visual Studio 2017 kullanılarak C# dilinde yazılmış bir .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 440ef2ed398b22262923422efd7f1259e3ee9b74
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633699"
---
# <a name="build-a-net-standard-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Bir .NET Standard kitaplığı ile derleme C# ve Visual Studio 2017'de .NET Core SDK'sı

A *sınıf kitaplığı* türlerini ve bir uygulama tarafından çağrılan yöntemlere tanımlar. .NET Standard 2.0 hedefleyen bir sınıf kitaplığı, .NET Standard sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılacak kitaplığınızı sağlar. Sınıf kitaplığınıza bitirdikten sonra bir üçüncü taraf bileşeni veya bir veya daha fazla uygulama ile birlikte gelen bir bileşeni olarak dahil etmek isteyip istemediğinizi olarak dağıtmak isteyip istemediğinize karar verebilirsiniz.

> [!NOTE]
> .NET Standard sürümleri ve destekledikleri platformlar listesi için bkz: [.NET Standard](../../standard/net-standard.md).

Bu konuda, tek bir dize işleme yöntemini içeren bir basit bir yardımcı program kitaplığı oluşturacaksınız. Olarak uygulayacaksınız bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) üyesi değilmiş gibi çağırabilirsiniz <xref:System.String> sınıfı.

## <a name="creating-a-class-library-solution"></a>Bir sınıf kitaplığı çözüm oluşturma

Sınıf kitaplığı projenizi ve ilgili projeleri çözüm oluşturmaya başlayın. Bir Visual Studio çözümü yalnızca bir veya daha fazla proje için kapsayıcı işlevi görür. Çözümü oluşturmak için:

1. Visual Studio menü çubuğunda **dosya** > **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda genişletin **diğer proje türleri** düğüm ve select **Visual Studio çözümleri**. Seçin ve "ClassLibraryProjects" çözümünü arlandırın **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu ile vurgulanmış yeni bir boş çözüm](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

Sınıf kitaplığı projenizi oluşturun:

1. İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözüm dosyası ve bağlam menüsünden seçin **Ekle** > **yeni Proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda genişletin **Visual C#** düğümünü seçip **.NET Standard** düğümünü ve ardından **sınıf kitaplığı (.NET Standard)** proje şablonu. İçinde **adı** metin kutusunda, projenin adı "StringLibrary" girin. Seçin **Tamam** sınıf kitaplığı projesi oluşturmak için.

   ![Yeni kitaplık projesi iletişim kutusu Ekle](./media/library-with-visual-studio/add-new-library-project.png)

   Kod penceresi, ardından Visual Studio geliştirme ortamında açar.

   ![Visual Studio uygulama penceresinin varsayılan sınıf kitaplığı şablonu kodu gösterme](./media/library-with-visual-studio/string-library-project.png)

1. Kitaplığımızı .NET Standard'ın doğru sürümü hedeflediğinden emin olun. Kitaplığı projesinde sağ **Çözüm Gezgini** windows, ardından **özellikleri**. **Hedef Framework'ü** metin kutusuna .NET Standard 2.0 hedeflediğiniz gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. Kod penceresinde kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Sınıf Kitaplığı `UtilityLibraries.StringLibrary`, adında bir yöntem içeriyorsa `StartsWithUpper`, döndüren bir <xref:System.Boolean> geçerli dize örneğinde bir büyük harf karakteri ile başlayan olup olmadığını gösteren değer. Unicode standardı, küçük harfli karakterlerden büyük harf karakterler ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Yöntemi döndürür `true` bir karakterin büyük harf ise.

1. Menü çubuğunda, seçin **derleme** > **Çözümü Derle**. Projenin hatasız derlemeniz gerekir.

   ![Derleme başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Sonraki adım

Kitaplık başarıyla oluşturdunuz. Yöntemlerinden herhangi biri olarak adlandırılan henüz olduğundan, beklendiği gibi çalıştığını bilmiyorum. Kullanarak test etmek için kitaplığınızın geliştirme sonraki adımı olan bir [Birim Test projesi](testing-library-with-visual-studio.md).
