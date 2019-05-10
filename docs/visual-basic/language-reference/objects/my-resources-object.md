---
title: My.Resources nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 02e29b17404da0e868973364b0b17b5c4ca418c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647624"
---
# <a name="myresources-object"></a>My.Resources Nesnesi
Uygulama kaynaklarına erişmek için özellikler ve sınıfları sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Resources` Nesne uygulamanın kaynaklara erişim sağlar ve uygulamanız için alma kaynakları dinamik olarak sağlar. Daha fazla bilgi için [uygulama kaynaklarını yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` Nesnesi yalnızca Genel kaynaklar kullanıma sunar. Forms ile ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarını formdan erişmeniz gerekir.  
  
 Uygulamanın kültüre özgü kaynak dosyalarından erişebileceğiniz `My.Resources` nesne. Varsayılan olarak, `My.Resources` kültürün eşleşen kaynak dosyasındaki kaynakları nesne şuna <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> özelliği. Ancak, bu davranışı geçersiz kılmak ve kaynaklar için kullanılacak belirli bir kültür belirtin. Daha fazla bilgi için [masaüstü uygulamalarında kaynakların](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Özellikler  
 Özelliklerini `My.Resources` nesnesi, uygulamanızdaki kaynaklarından salt okunur erişim sağlar. Kaynak ekleme veya kaldırma için kullanın **Proje Tasarımcısı**. İle eklenen kaynaklar erişebileceğiniz **Proje Tasarımcısı** kullanarak `My.Resources.` *resourceName*.  
  
 Ayrıca ekleyebilir veya projenizdeki seçerek kaynak dosyaları kaldırmak **Çözüm Gezgini** tıklayıp **Yeni Öğe Ekle** veya **varolan öğeyi Ekle** gelen  **Proje** menüsü. Bu şekilde kullanılarak eklenen kaynaklara erişebilir `My.Resources.` *resourceFileName*`.`*resourceName*.  
  
 Her kaynak bir ad, kategori ve değere sahip ve bu kaynak ayarlarını kaynağa erişmek için özelliği nasıl görünür `My.Resources` nesne. Eklenen kaynaklar için **Proje Tasarımcısı**:  
  
- Özelliğin adını belirleyen adı  
  
- Kaynak veri özelliğinin değeri olan  
  
- Kategori özelliğinin türü belirler:  
  
|Kategori|Özellik verilerinin türü|  
|---|---|  
|**Dizeler**|[Dize](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Görüntüler**|<xref:System.Drawing.Bitmap>|  
|**Simgeler**|<xref:System.Drawing.Icon>|  
|**Ses**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> Sınıf türetilir <xref:System.IO.Stream> akışları gibi ele yöntemleriyle kullanılabilmesi için sınıf <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> yöntemi.|  
|**Dosyalar**|-   [Dize](../../../visual-basic/language-reference/data-types/string-data-type.md) metin dosyaları için.<br />-   <xref:System.Drawing.Bitmap> resim dosyaları.<br />-   <xref:System.Drawing.Icon> simge dosyaları için.<br />-   <xref:System.IO.UnmanagedMemoryStream> ses dosyaları için.|  
|**Diğer**|Tasarımcının bilgileri tarafından belirlenen **türü** sütun.|  
  
## <a name="classes"></a>Sınıflar  
 `My.Resources` Nesne paylaşılan özelliklere sahip bir sınıf olarak her kaynak dosyası sunar. Sınıf adı, kaynak dosyasının adı ile aynıdır. Önceki bölümde açıklandığı gibi bir kaynak dosyasındaki kaynakları sınıfı özellikleri olarak sunulur.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir formun başlık adlı dize kaynağı ayarlar `Form1Title` içinde uygulama kaynak dosyası. Örneğin çalışması, uygulama adlı bir dize olmalıdır `Form1Title` kaynak dosyasındaki.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Bu örnek form simgesini adlı simgesi ayarlar `Form1Icon` uygulamanın kaynak dosyasında depolanır. Örneğin çalışması, uygulama adlı bir simge olmalıdır `Form1Icon` kaynak dosyasındaki.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir görüntü kaynağı için bir form arka plan görüntüsü ayarlar `Form1Background`, uygulama kaynak dosyasına olduğu. Bu örneğin çalışması, uygulama adlı bir görüntü kaynağı olmalıdır `Form1Background` kaynak dosyasındaki.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir ses kaynak olarak depolanan ses çalar `Form1Greeting` uygulamanın kaynak dosya. Örneğin çalışması, uygulama adlı bir ses kaynağı olmalıdır `Form1Greeting` kaynak dosyasındaki. `My.Computer.Audio.Play` Yöntemi yalnızca Windows Forms uygulamaları için kullanılabilir.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dize kaynağı uygulamanın kültürünü Fransızca sürümü alır. Kaynak adında `Message`. Kültürü değiştirme, `My.Resources` nesnesini kullanır, örnekte <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Bu örneğin çalışması, uygulama adlı bir dize olmalıdır `Message` Resources.fr-FR.resx bu kaynak dosyanın kültürünü Fransızca sürümü, kaynak dosya ve uygulama olması gerekir. Uygulama kaynak dosyanın kültürünü Fransızca sürümü yoksa `My.Resource` nesne kaynak varsayılan kültür kaynak dosyasından alır.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Kaynaklarını Yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../framework/resources/index.md)
