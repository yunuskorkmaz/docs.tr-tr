---
title: Visual Basic ve Visual Studio 2017'de .NET Core ile bir sınıf kitaplığı oluşturma
description: Visual Studio 2017'yi kullanarak Visual Basic'te yazılmış bir sınıf kitaplığı derleme hakkında bilgi edinin
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52bbae330afe4a9ea376c6388a06941f74f6606a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591639"
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a>Visual Basic ve Visual Studio 2017'de .NET Core ile bir sınıf kitaplığı oluşturma

A *sınıf kitaplığı* türlerini ve bir uygulama tarafından çağrılan yöntemlere tanımlar. .NET Standard 2.0 hedefleyen bir sınıf kitaplığı, .NET Standard sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılacak kitaplığınızı sağlar. Sınıf kitaplığınıza bitirdikten sonra bir üçüncü taraf bileşeni veya bir veya daha fazla uygulama ile birlikte gelen bir bileşeni olarak dahil etmek isteyip istemediğinizi olarak dağıtmak isteyip istemediğinize karar verebilirsiniz.

> [!NOTE]
> .NET Standard sürümleri ve destekledikleri platformlar listesi için bkz: [.NET Standard](../../standard/net-standard.md).

Bu konuda, tek bir dize işleme yöntemini içeren bir basit bir yardımcı program kitaplığı oluşturacaksınız. Olarak uygulayacaksınız bir [genişletme yöntemi](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) üyesi değilmiş gibi çağırabilirsiniz <xref:System.String> sınıfı.

## <a name="creating-a-class-library-solution"></a>Bir sınıf kitaplığı çözüm oluşturma

Sınıf kitaplığı projenizi ve ilgili projeleri çözüm oluşturmaya başlayın. Bir Visual Studio çözümü yalnızca bir veya daha fazla proje için kapsayıcı işlevi görür. Çözümü oluşturmak için:

1. Visual Studio menü çubuğunda **dosya** > **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda genişletin **diğer proje türleri** düğüm ve select **Visual Studio çözümleri**. Seçin ve "ClassLibraryProjects" çözümünü arlandırın **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

Sınıf kitaplığı projenizi oluşturun:

1. İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözüm dosyası ve bağlam menüsünden seçin **Ekle** > **yeni Proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda genişletin **Visual Basic** düğümünü seçip **.NET Standard** düğümünü ve ardından **sınıf kitaplığı (.NET Standard)**  proje şablonu. İçinde **adı** metin kutusunda, projenin adı "StringLibrary" girin. Seçin **Tamam** sınıf kitaplığı projesi oluşturmak için.

   ![Yeni Proje iletişim kutusu Ekle](./media/vb-library-with-visual-studio/libproject.png)

   Kod penceresi, ardından Visual Studio geliştirme ortamında açar. 
 
   ![Visual Studio uygulama penceresinin varsayılan sınıf kitaplığı şablonu kodu gösterme](./media/vb-library-with-visual-studio/stringlibrary.png)

1. Kitaplık .NET Standard doğru sürümünü hedefleyen emin olun. Kitaplığı projesinde sağ **Çözüm Gezgini** windows, ardından **özellikleri**. **Hedef Framework'ü** metin kutusuna .NET Standard 2.0 hedeflediğiniz gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/properties.png)

1. Ayrıca **özellikleri** iletişim kutusunda, metni silmek **kök ad alanı** metin kutusu. Her proje için Visual Basic proje adına karşılık gelen bir ad alanı otomatik olarak oluşturur ve bu ad alanının üst kaynak kodu dosyalarında tanımlanan tüm ad alanları olan. Kullanarak bir en üst düzey ad alanı tanımlamak istediğimiz [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğü.
  
1. Kod penceresinde kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Sınıf Kitaplığı `UtilityLibraries.StringLibrary`, adında bir yöntem içeriyorsa `StartsWithUpper`, döndüren bir <xref:System.Boolean> geçerli dize örneğinde bir büyük harf karakteri ile başlayan olup olmadığını gösteren değer. Unicode standardı, küçük harfli karakterlerden büyük harf karakterler ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Yöntemi döndürür `true` bir karakterin büyük harf ise.

1. Menü çubuğunda, seçin **derleme** > **Çözümü Derle**. Projenin hatasız derlemeniz gerekir.

   ![Derleme başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a>Sonraki adım

Kitaplık başarıyla oluşturdunuz. Yöntemlerinden herhangi biri olarak adlandırılan henüz olduğundan, beklendiği gibi çalıştığını bilmiyorum. Kullanarak test etmek için kitaplığınızın geliştirme sonraki adımı olan bir [Birim Test projesi](testing-library-with-visual-studio.md).
