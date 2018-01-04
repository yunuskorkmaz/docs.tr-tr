---
title: My.Resources Nesnesi
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords: My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e5b909d9945ed631cebe07e4cfc7d5dc2e019f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="myresources-object"></a>My.Resources Nesnesi
Uygulamanın kaynaklarına erişmek için özellikler ve sınıfları sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Resources` Nesne uygulamanın kaynaklarına erişmesini sağlar ve uygulamanız için alma kaynakları dinamik olarak sağlar. Daha fazla bilgi için bkz: [yönetme uygulama kaynakları (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` Nesne yalnızca Genel kaynaklar kullanıma sunar. Formları ile ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarını formdan erişmeniz gerekir.  
  
 Uygulamanın kültüre özgü kaynak dosyalarından erişebilirsiniz `My.Resources` nesnesi. Varsayılan olarak, `My.Resources` nesne görünür kültürün eşleşen kaynak dosyasındaki kaynakları <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> özelliği. Ancak, bu davranışı geçersiz kılmak ve kaynaklarını kullanmak için belirli bir kültür belirtin. Daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Özellikler  
 Özelliklerini `My.Resources` nesnesi, uygulamanızın kaynakları salt okunur erişim sağlar. Eklemek veya kaynakları kaldırmak için kullanın **Proje Tasarımcısı**. Aracılığıyla eklenen kaynaklara erişebilir **Proje Tasarımcısı** kullanarak `My.Resources.``resourceName`.  
  
 Ayrıca ekleyebilir veya kaynak dosyalarını projenizde seçerek kaldırmak **Çözüm Gezgini** tıklatıp **Yeni Öğe Ekle** veya **varolan öğeyi Ekle** gelen  **Proje** menüsü. Bu şekilde kullanılarak eklenen kaynaklara erişebilir `My.Resources.``resourceFileName`.`resourceName`.  
  
 Her bir kaynağın ad, kategori ve değer var ve bu kaynak ayarları kaynağa erişmek için özellik nasıl görünür belirlemek `My.Resources` nesnesi. Eklenen kaynaklar için **Proje Tasarımcısı**:  
  
-   Name özelliği adını belirler,  
  
-   Kaynak verileri özelliği değeri,  
  
-   Kategori özelliği türünü belirler:  
  
|Kategori|Özellik veri türü|  
|---|---|  
|**Dizeler**|[Dize](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Görüntüler**|<xref:System.Drawing.Bitmap>|  
|**Simgeler**|<xref:System.Drawing.Icon>|  
|**Ses**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> Sınıfı türer <xref:System.IO.Stream> akışlar, gibi ele yöntemleriyle kullanılabilmesi için sınıf <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> yöntemi.|  
|**Dosyaları**|-   [Dize](../../../visual-basic/language-reference/data-types/string-data-type.md) metin dosyaları için.<br />-   <xref:System.Drawing.Bitmap>resim dosyaları.<br />-   <xref:System.Drawing.Icon>simge dosyaları.<br />-   <xref:System.IO.UnmanagedMemoryStream>ses dosyaları.|  
|**Diğer**|Tasarımcının bilgileri tarafından belirlenen **türü** sütun.|  
  
## <a name="classes"></a>Sınıflar  
 `My.Resources` Nesne paylaşılan özelliklerle bir sınıf olarak her kaynak dosyası gösterir. Sınıf adı kaynak dosyasının adı ile aynıdır. Önceki bölümde açıklandığı gibi bir kaynak dosyası kaynaklarında sınıfındaki özellikleri olarak sunulur.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir form başlığı adlı dize kaynağı ayarlar `Form1Title` uygulama kaynak dosyasında. Örneğin çalışması, uygulamanın adlı bir dize olması gerekir `Form1Title` kendi kaynak dosyasında.  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnek form simgesini adlı simgesi ayarlar `Form1Icon` uygulamanın kaynak dosyasında depolanır. Örneğin çalışması, uygulamanın adlı bir simge olması gerekir `Form1Icon` kendi kaynak dosyasında.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir form arka plan görüntüsü adlı görüntü kaynağı ayarlar `Form1Background`, uygulama kaynak dosyasında olduğu. Bu örnekte çalışması, uygulama adlı bir görüntü kaynağı olmalıdır `Form1Background` kendi kaynak dosyasında.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir ses kaynağı depolanan ses çalar `Form1Greeting` uygulamanın kaynak dosyasında. Örneğin çalışması, uygulama adlı bir ses kaynağı olmalıdır `Form1Greeting` kendi kaynak dosyasında. `My.Computer.Audio.Play` Yöntemi yalnızca Windows Forms uygulamaları için kullanılabilir.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte uygulamanın bir dize kaynağı Fransızca kültür sürümünü alır. Kaynak adlı `Message`. Kültür değiştirmek için `My.Resources` nesnesini kullanan, örnek kullanır <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Bu örnekte çalışması, uygulamanın adlı bir dize olması gerekir `Message` kendi kaynak dosya ve uygulama bu kaynak dosyası Resources.fr FR.resx Fransızca kültür sürümüne sahip olmalıdır. Uygulama kaynak dosyası kültür Fransızca sürümü yoksa `My.Resource` nesnesi varsayılan kültürü kaynak dosyasından kaynak alır.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Kaynaklarını Yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../framework/resources/index.md)  

