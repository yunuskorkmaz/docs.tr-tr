---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211414"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme

Windows Forms uygulamanız için formlar ve denetimler oluşturmak gibi art arda gerçekleştirir çok sayıda görev vardır. Karşınıza çıkacak sık gerçekleştirilen görevlerin bazıları şunlardır:

- Ekleyerek veya bir sekme üzerindeki kaldırarak bir <xref:System.Windows.Forms.TabControl>.

- Bir denetim için üst yerleştirme.

- Yönünü değiştirme bir <xref:System.Windows.Forms.SplitContainer> denetimi.

Geliştirme hızlandırmak için pek çok denetimi tasarım zamanında bu tek gibi genel görevleri gerçekleştirmenize olanak tanıyan bağlama duyarlı menüler şunlardır akıllı etiketler sunar. Bu görevleri adlı *akıllı etiket fiilleri*.

Akıllı etiketler Tasarımcısı'nda yaşam süresi'için bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

- Bir Windows Forms projesi oluşturma

- Akıllı etiketleri kullanarak

- Akıllı etiketler devre dışı bırakma ve etkinleştirme

İşlemi tamamladığınızda, bu önemli bir düzen özellikleri tarafından oynadığı rol, bir anlayışa sahip olacaksınız.

## <a name="create-the-project"></a>Projeyi oluşturma

İlk adım projeyi oluşturmak ve formu ayarlamaktır.

1. Visual Studio'da "SmartTagsExample" adlı bir Windows tabanlı uygulama projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms Uygulama**).

2. Formda seçin **Windows Form Tasarımcısı**.

## <a name="use-smart-tags"></a>Akıllı etiketler kullanın.

Akıllı etiketler her zaman bunları teklif denetimleri tasarım zamanında kullanılabilir.

1. Sürükleme bir <xref:System.Windows.Forms.TabControl> gelen **araç kutusu** formunuza. Akıllı etiket karakterini unutmayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) üzerinde yan, görüntülenen <xref:System.Windows.Forms.TabControl>.

2. Akıllı etiket karakterini tıklayın. Glif yanında görüntülenen kısayol menüsünden seçin **Sekme Ekle** öğesi. Yeni bir sekme sayfası eklenir gözlemleyin <xref:System.Windows.Forms.TabControl>.

3. Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.

4. Akıllı etiket karakterini tıklayın. Glif yanında görüntülenen kısayol menüsünden seçin **Sütun Ekle** öğesi. Yeni bir sütun eklenir gözlemleyin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.

5. Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi **araç kutusu** formunuza.

6. Akıllı etiket karakterini tıklayın. Glif yanında görüntülenen kısayol menüsünden seçin **Yatay bölümlendirici yönlendirmesini** öğesi. Mesajının görüntülendiğini görün <xref:System.Windows.Forms.SplitContainer> denetimin ayırıcıyı, artık yatay odaklıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [İzlenecek yol: Bir Windows Formları bileşenine akıllı etiket ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))
