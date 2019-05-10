---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e34785fce3cd88bfe4fe4b075ba34b8d22bff4
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469644"
---
# <a name="how-to-create-com-wrappers"></a>Nasıl yapılır: COM Sarmalayıcıları Oluşturma

Bileşen Nesne Modeli (COM) sarmalayıcılar Visual Studio 2005 özellikleri veya .NET Framework Araçları, Tlbimp.exe ve RegAsm.exe'yi kullanarak oluşturabilirsiniz. Her iki yöntem de iki tür COM sarmalayıcıları oluşturma:

- A [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) COM nesnesinin yönetilen kodu çalıştırmak için bir tür kitaplığından.

- A [COM çağrılabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md) ile yönetilen bir nesneye yerel bir uygulamada çalıştırmak için gerekli kayıt defteri ayarları.

Visual Studio 2005'te, projenize bir başvuru olarak COM sarmalayıcı ekleyebilirsiniz.

## <a name="wrap-com-objects-in-a-managed-application"></a>Yönetilen bir uygulamada COM nesneleri Kaydır

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için

1. Yönetilen uygulamanız için projeyi açın.

2. Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.

3. Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.

4. Başvuru Ekle iletişim kutusuna tıklayın **COM** sekmesinde, seçmek istediğiniz tıklatın ve bileşeni **Tamam**.

     İçinde **Çözüm Gezgini**, projenizi başvurular klasörüne COM bileşeninin eklendiğine dikkat edin.

Artık, COM nesnesi erişmek için kod yazabilirsiniz. Nesne gibi ile bildirerek başlayın bir `Imports` Visual Basic için ifade veya `Using` bildirimi C#.

> [!NOTE]
> Program için Microsoft Office bileşenleri istiyorsanız, önce yükleme [Microsoft Office birincil birlikte çalışma derlemeleri](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) gelen Microsoft Download Center. 4. adımda Nesne Kitaplığı gibi yüklemek istediğiniz Office ürün için kullanılabilen en son sürümünü seçin **Microsoft Word 11.0 Nesne Kitaplığı**.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>.NET Framework Araçları'nı kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için  
  
- Çalıştırma [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) aracı.  
  
 Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verileri içeren bir derleme oluşturur.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Yerel bir uygulamada yönetilen nesneleri saran  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak COM çağrılabilir sarmalayıcısı oluşturmak için  
  
1. Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için bir sınıf kitaplığı projesi oluşturun. Sınıfı, bir varsayılan oluşturucuya sahip olmalıdır.  
  
     AssemblyInfo dosyası içinde derleme için bir tam Dört bölümlü sürüm numarasına sahip olduğunuzu doğrulayın. Bu sayı, sürüm oluşturma Windows kayıt defterinde bakımı için gereklidir. Sürüm numaraları hakkında daha fazla bilgi için bkz: [derleme sürümlendirme](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
3. Tıklayın **derleme** sekmesi.  
  
4. Seçin **kaydetme COM birlikte çalışması için** onay kutusu.  
  
 Proje oluşturduğunuzda, derlemenin COM birlikte çalışması için otomatik olarak kaydedilir. Visual Studio 2005 yerel bir uygulama oluşturuyorsanız tıklayarak derleme kullanabilirsiniz **Başvuru Ekle** üzerinde **proje** menüsü.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçları kullanarak COM çağrılabilir sarmalayıcısı oluşturmak için  
  
Çalıştırma [Regasm.exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) aracı.  
  
Bu araç, derleme meta verileri okur ve kayıt defterine gerekli girişleri ekler. Sonuç olarak, COM istemcilerinin şeffaf bir şekilde .NET Framework sınıfları oluşturabilirsiniz. Yerel bir COM sınıfı gibi derleme kullanabilirsiniz.  
  
Herhangi bir dizinde bulunan bir derlemeyi Regasm.exe çalıştırın ve ardından çalıştırın [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel bütünleştirilmiş kod önbelleğine taşıyın. Derleme başka bir yerde bulunamazsa genel derleme önbelleği her zaman incelenir çünkü derleme taşıma konumu, kayıt defteri girdilerini geçersiz kılmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanında Çağrılabilir Sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md)
- [COM Çağrılabilir Sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md)
