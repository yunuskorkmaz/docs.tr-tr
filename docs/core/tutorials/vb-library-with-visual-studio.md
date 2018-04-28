---
title: Visual Basic ve Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı oluşturma
description: Visual Studio 2017 kullanarak Visual Basic'te yazılmış bir sınıf kitaplığı oluşturmayı öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: 149be4788d924afee8affc816eede075cbe4e3a1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a>Visual Basic ve Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı oluşturma

A *sınıf kitaplığı* türleri ve bir uygulama tarafından çağrılan yöntemleri tanımlar. .NET standart 2.0 hedefleyen bir sınıf kitaplığı .NET standart bu sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılması için kitaplığınızın sağlar. Sınıf kitaplığı bitirdikten sonra bir üçüncü taraf bileşeni veya bir veya daha fazla uygulama ile birlikte gelen bir bileşeni olarak dahil etmek isteyip istemediğinizi olarak dağıtmak isteyip istemediğinize karar verebilirsiniz.

> [!NOTE]
> .NET standart sürümleri ve desteklenen platformlar listesi için bkz: [.NET standart](../../standard/net-standard.md).

Bu konuda, tek bir dize işleme yöntemi içeren basit yardımcı programı kitaplığı oluşturacaksınız. Olarak uygulamanız bir [genişletme yöntemi](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) üyesi değilmiş gibi çağırabilirsiniz böylece <xref:System.String> sınıfı.

## <a name="creating-a-class-library-solution"></a>Bir sınıf kitaplığı çözümü oluşturma

Sınıf kitaplığı projenizin ve ilgili projeleri için bir çözüm oluşturmaya başlayın. Visual Studio çözümü, yalnızca bir veya daha fazla projeleri için bir kapsayıcı olarak görev yapar. Çözüm oluşturmak için:

1. Visual Studio menü çubuğunda seçin **dosya** > **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda, genişletin **diğer proje türleri** düğümü ve select **Visual Studio çözümleri**. "ClassLibraryProjects" Çözüm adı ve seçin **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

Sınıf kitaplığı projenizin oluşturun:

1. İçinde **Çözüm Gezgini**, sağ tıklayın **ClassLibraryProjects** çözüm dosya ve bağlam menüsünden seçin **Ekle** > **yeni Proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual Basic** düğümünü, ardından **.NET standart** düğümünü ve ardından **sınıf kitaplığı (.NET standart)**  proje şablonu. İçinde **adı** metin kutusunda, "StringLibrary" projesinin adı girin. Seçin **Tamam** sınıf kitaplığı proje oluşturmak için.

   ![Yeni Proje iletişim kutusu ekleme](./media/vb-library-with-visual-studio/libproject.png)

   Kod penceresi ardından Visual Studio geliştirme ortamında açar. 
 
   ![Visual Studio uygulama penceresi varsayılan sınıf kitaplığı şablonu kodu gösterme](./media/vb-library-with-visual-studio/stringlibrary.png)

1. Kitaplığı .NET standart doğru sürümü hedefleyen emin olmak için kontrol edin. Kitaplık projeye sağ tıklayın **Çözüm Gezgini** windows, ardından **özellikleri**. **Hedef Framework** metin kutusu gösterir biz .NET standart 2.0 hedefleme.

   ![Sınıf kitaplığı proje özellikleri](./media/library-with-visual-studio/properties.png)

1. De **özellikleri** iletişim kutusunda, metin temizleyin **kök ad alanı** metin kutusu. Her proje için Visual Basic proje adına karşılık gelen bir ad alanı otomatik olarak oluşturur ve bu ad alanının üst kaynak kodu dosyaları içinde tanımlanan tüm ad alanlarını şunlardır. En üst düzey bir ad kullanarak tanımlamak istiyoruz [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğü.
  
1. Kod penceresinde kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Sınıf Kitaplığı `UtilityLibraries.StringLibrary`, adlandırılmış bir yöntem içerir `StartsWithUpper`, döndüren bir <xref:System.Boolean> geçerli dize örneği bir büyük harf karakter ile başlayan olup olmadığını belirten değer. Unicode standart büyük harfli karakterler, küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Yöntemi döndürür `true` bir karakter büyük harf ise.

1. Menü çubuğunda seçin **yapı** > **yapı çözümü**. Proje derleme hatası.

   ![Yapı başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a>Sonraki adım

Kitaplık başarıyla temel aldık. Yöntemlerinden herhangi biri adlı henüz olduğundan, beklendiği gibi çalışıp çalışmadığını bilinmiyor. Kitaplığınızı geliştirme sonraki adım kullanarak test etmektir bir [birim testi projesi](testing-library-with-visual-studio.md).
