---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e10b6fd7df003de739b57bbb3e17deb46215763f
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363995"
---
# <a name="how-to-create-com-wrappers"></a>Nasıl yapılır: COM Sarmalayıcıları Oluşturma

Visual Studio 2005 özelliklerini veya .NET Framework araçları Tlbimp. exe ve Regasm. exe ' yi kullanarak bileşen nesne modeli (COM) sarmalayıcıları oluşturabilirsiniz. Her iki yöntem de iki tür COM sarmalayıcıları üretir:

- Yönetilen kodda bir COM nesnesi çalıştırmak için bir tür kitaplığından bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) .

- Yerel bir uygulamada yönetilen bir nesne çalıştırmak için gerekli kayıt defteri ayarlarına sahip [com çağrılabilir sarmalayıcı](../../../docs/framework/interop/com-callable-wrapper.md) .

Visual Studio 2005 ' de COM sarmalayıcısı ' ı projenize bir başvuru olarak ekleyebilirsiniz.

## <a name="wrap-com-objects-in-a-managed-application"></a>Yönetilen bir uygulamadaki COM nesnelerini sarın

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için

1. Yönetilen uygulamanız için projeyi açın.

2. **Proje** menüsünde **tüm dosyaları göster**' e tıklayın.

3. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

4. Başvuru Ekle iletişim kutusunda, **com** sekmesine tıklayın, kullanmak istediğiniz bileşeni seçin ve **Tamam**' a tıklayın.

     **Çözüm Gezgini**, com bileşeninin projenizdeki başvurular klasörüne eklendiğini unutmayın.

Artık COM nesnesine erişmek için kod yazabilirsiniz. Nesnesini bildirerek, örneğin, Visual Basic için bir `Imports` deyimle veya bir `Using` bildirimi ile başlayabilirsiniz. C#

> [!NOTE]
> Microsoft Office bileşenleri programlamak istiyorsanız, önce Microsoft Indirme merkezi 'nden [Microsoft Office birincil birlikte çalışma derlemelerini](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) yükleyin. 4\. adımda, **Microsoft Word 11,0 nesne kitaplığı**gibi istediğiniz Office ürünü için uygun nesne kitaplığının en son sürümünü seçin.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçlarını kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için  
  
- [Tlbimp. exe (tür kitaplığı Içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) aracını çalıştırın.  
  
 Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verilerini içeren bir derleme oluşturur.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Yönetilen nesneleri yerel bir uygulamada sarın  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için  
  
1. Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için bir sınıf kitaplığı projesi oluşturun. Sınıf parametresiz bir oluşturucuya sahip olmalıdır.  
  
     AssemblyInfo dosyasında derlemelerinizin dört bölümden oluşan tam bir sürüm numarasına sahip olduğunuzu doğrulayın. Bu sayı, Windows kayıt defterinde sürüm oluşturmayı sürdürmek için gereklidir. Sürüm numaraları hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
3. **Derle** sekmesine tıklayın.  
  
4. **Com birlikte çalışması Için kaydol** onay kutusunu seçin.  
  
 Projeyi derlediğinizde, derleme otomatik olarak COM birlikte çalışma için kaydedilir. Visual Studio 2005 ' de yerel bir uygulama oluşturuyorsanız, **Proje** menüsünde **Başvuru Ekle** ' ye tıklayarak derlemeyi kullanabilirsiniz.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçlarını kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için  
  
[Regasm. exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) aracını çalıştırın.  
  
Bu araç derleme meta verilerini okur ve gerekli girdileri kayıt defterine ekler. Sonuç olarak, COM istemcileri .NET Framework sınıfları saydam şekilde oluşturabilir. Derlemeyi yerel bir COM sınıfı gibi kullanabilirsiniz.  
  
Herhangi bir dizinde bulunan bir derlemede Regasm. exe ' yi çalıştırabilir ve ardından [Gacutil. exe ' yi (genel bütünleştirilmiş kod önbelleği aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) çalıştırarak genel derleme önbelleğine taşıyabilirsiniz. Derlemenin taşınması konum kayıt defteri girdilerini geçersiz kılmaz, çünkü derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanında Çağrılabilir Sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md)
- [COM Çağrılabilir Sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md)
