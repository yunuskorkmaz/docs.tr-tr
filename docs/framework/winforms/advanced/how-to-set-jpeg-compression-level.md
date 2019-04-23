---
title: 'Nasıl yapılır: JPEG Sıkıştırma Düzeyini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: de9dce1b3c15070fda268c430ce5da641efef6f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130682"
---
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="27169-102">Nasıl yapılır: JPEG Sıkıştırma Düzeyini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="27169-102">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="27169-103">Dosya boyutu en aza indirmek ve yazılımınızın kalitesini iyileştirmek için diske görüntüyü kaydederken görüntü parametrelerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27169-103">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="27169-104">Bir JPEG görüntüsünü kalitesini, sıkıştırma düzeyi değiştirerek ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27169-104">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="27169-105">Bir JPEG görüntüsünü kaydettiğinizde sıkıştırma düzeyini belirtmek için oluşturmalısınız bir <xref:System.Drawing.Imaging.EncoderParameters> nesne ve geçirin <xref:System.Drawing.Image.Save%2A> yöntemi <xref:System.Drawing.Image> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27169-105">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="27169-106">Başlatma <xref:System.Drawing.Imaging.EncoderParameters> BT'nin aşağıdakilerden birini oluşturan bir dizi bu nesne <xref:System.Drawing.Imaging.EncoderParameter>.</span><span class="sxs-lookup"><span data-stu-id="27169-106">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="27169-107">Oluştururken <xref:System.Drawing.Imaging.EncoderParameter>, belirtin <xref:System.Drawing.Imaging.Encoder.Quality> Kodlayıcısı ve istenen sıkıştırma düzeyi.</span><span class="sxs-lookup"><span data-stu-id="27169-107">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27169-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="27169-108">Example</span></span>  
 <span data-ttu-id="27169-109">Aşağıdaki örnek kod oluşturur bir <xref:System.Drawing.Imaging.EncoderParameter> nesne ve üç JPEG görüntüleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="27169-109">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="27169-110">Değiştirerek farklı kalite düzeyiyle, kaydedilen her bir JPEG görüntüsünü `long` geçirilen değer <xref:System.Drawing.Imaging.EncoderParameter> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="27169-110">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="27169-111">0 kalite düzeyini, en yüksek sıkıştırma karşılık gelir ve bir kalite düzeyi 100 için en az sıkıştırma karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="27169-111">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27169-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="27169-112">Compiling the Code</span></span>  
 <span data-ttu-id="27169-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="27169-113">This example requires:</span></span>  
  
-   <span data-ttu-id="27169-114">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="27169-114">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="27169-115">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="27169-115">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
-   <span data-ttu-id="27169-116">Adlı bir resim dosyası `TestPhoto.jpg` ve konumunda bulunan **c:\\**.</span><span class="sxs-lookup"><span data-stu-id="27169-116">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27169-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27169-117">See also</span></span>

- [<span data-ttu-id="27169-118">Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme</span><span class="sxs-lookup"><span data-stu-id="27169-118">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [<span data-ttu-id="27169-119">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="27169-119">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="27169-120">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="27169-120">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
